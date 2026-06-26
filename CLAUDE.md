# Traknova Content Pipeline

## What this project is
An autonomous multi-agent content writing pipeline for Traknova. It takes a completed content brief and produces a research-backed, ICP-aligned, search-optimised article draft ready for human review. Every agent in the pipeline is purpose-built for one job and passes a shared context object to the next stage. No agent works in isolation.

## Who built this and why
Built by Sheriff (Growth Marketer, Traknova) to produce content that is useful to the reader, trusted by search engines, and citable by LLMs. The pipeline removes the bottleneck of manual research and first drafting while preserving Traknova's voice, ICP specificity, and brand position at every stage.

## Who this content is for
Traknova's ICPs:
- PCO Operator
- Taxi Company Owner
- Car Rental Firm Owner
- Car Dealership Owner or Manager
- Field Services Fleet Manager
- Logistics Fleet Manager

ICP profiles are stored in context/traknova-context/ and are loaded by agents at runtime.

## Pipeline stages
The pipeline runs six agents in sequence. Each agent receives the context object, does its job, updates the context object, and passes it forward.

1. Brief intake — reads the completed content brief from briefs/, extracts all relevant fields, and builds the context object
2. Research agent — constructs targeted search queries per section and executes them via Serper (Google) and Apify (Reddit). Returns raw research findings with credibility scores.
3. Analysis agent — scores every finding against three criteria: ICP relevance, Traknova POV alignment, and section coverage. Filters findings and flags data gaps.
4. Synthesis agent — transforms filtered findings into structured key points per section and builds the narrative thread for the full article
5. Writing agent — writes the article section by section using key points and narrative thread. Maintains a rolling draft context window to ensure continuity.
6. QA agent — performs a full quality check across flow, tone, ICP alignment, and content gaps. Produces a structured QA report and a final recommendation.

After the QA agent, the article goes to human review.

## Folder structure
- briefs/ — completed content briefs, one file per article. Copy brief-template.md, fill it in, and save it here before running the pipeline.
- agents/ — one folder per agent, numbered in pipeline order. Each folder contains prompt.md and a skills/ subfolder where applicable.
- context/ — shared context files used by every agent at runtime
  - traknova-context/ — ICP profiles, brand POV, and shared context schema
- outputs/ — completed article drafts after QA, one file per article
- logs/ — pipeline run logs for debugging

## Agent skills
Skills are sub-instructions loaded by specific agents to handle specific tasks. They are stored in the skills/ subfolder of each agent.

Research agent skills:
- construct-search-queries.md — builds targeted Serper and Apify queries per section using ICP context and intent signals derived from section headings
- evaluate-source-credibility.md — scores every research finding on a 1 to 5 credibility scale with classification and notes

Analysis agent skills:
- score-icp-relevance.md — scores each finding against the target ICP profile on a 1 to 5 scale
- detect-traknova-pov-conflict.md — flags findings that conflict with or undermine Traknova's brand position
- identify-data-gaps.md — assesses section-level research coverage and flags insufficient sections

Synthesis agent skills:
- evaluate-source-value.md — assigns a usage role to each filtered finding: primary claim, supporting evidence, real world example, counter and resolve, background context, or do not use
- extract-key-points.md — extracts 2 to 4 structured key points per section from filtered findings
- build-narrative-thread.md — constructs the full article narrative thread: central argument, section map, opening intent, closing intent, and transition logic

Writing agent skills:
- write-headline.md — produces three headline options with recommended choice, primary keyword placement, and search intent alignment
- write-introduction.md — writes the opening section with ICP validation, argument signalling, credibility establishment, and search/LLM visibility built in
- write-body-section.md — writes each body section using key points, narrative role, rolling draft context, and search/LLM visibility rules
- write-conclusion.md — writes the closing section landing the central argument, connecting to the ICP's conversion goal, and giving the reader a specific next step
- storytelling.md — quality check applied to every section: specificity, AI pattern detection, ICP voice, show-don't-label, narrative momentum, and LLM citability

QA agent skills:
- check-flow.md — assesses opening effectiveness, section transitions, argument progression, repetition, and closing effectiveness
- check-tone.md — checks UK English compliance, em dash violations, corporate jargon, AI pattern, peer-level tone, tone consistency, and filler language
- check-icp-alignment.md — checks reader identification, pain alignment, belief alignment, objection handling, language alignment, and conversion goal alignment
- flag-gaps.md — identifies unsupported claims, logical gaps, unanswered questions, skipped sections, founder review requirements, and search/LLM visibility gaps

## Shared context object
The shared context object is the backbone of the pipeline. It is built by the brief intake agent and updated by every subsequent agent. It travels through all six stages and ensures no agent works without full knowledge of what came before.

Key fields:
- run_id — unique identifier for this pipeline run
- article_goal — the full goal of the article extracted from the brief
- traknova_pov — Traknova's position on this article's topic
- icp_profile — the target ICP or ICPs for this article
- icp_supplementary_context — additional ICP context from the brief specific to this article
- narrative_thread — built by the synthesis agent, used by the writing agent
- sections — array of section objects, each carrying search queries, research findings, filtered findings, key points, and draft
- full_draft_so_far — updated after every section is written
- seo_context — keyword, intent, word count, meta data, and GEO/AEO checklist
- qa_notes — QA report produced by the QA agent
- pipeline_stage — current stage, updated by each agent before passing forward
- run_log — one-line entries appended by each agent on completion

The schema is in context/traknova-context/shared-context-schema.json.

## Context files
All standing context files are in context/traknova-context/:
- shared-context-schema.json — the structure of the context object
- icp-pco-operators.json — PCO Operator ICP profile
- icp-taxi-companies.json — Taxi Company Owner ICP profile
- icp-car-rental.json — Car Rental Firm Owner ICP profile
- icp-dealerships.json — Car Dealership Owner or Manager ICP profile
- icp-field-services.json — Field Services Fleet Manager ICP profile
- icp-logistics.json — Logistics Fleet Manager ICP profile
- brand-pov.md — Traknova's core beliefs, differentiators, standing positions, and content guidelines

## How to run the pipeline

### Before running
1. Copy briefs/brief-template.md and rename it for this article
2. Complete every section of the brief including the sign-off checklist
3. Confirm the Anthropic API key is authenticated
4. Confirm Serper.dev API key is available for the research agent
5. Confirm Apify API key is available for the research agent

### Running the pipeline
The pipeline is orchestrated via n8n. Each agent is a separate n8n workflow node that:
1. Receives the context object from the previous stage
2. Loads its prompt.md and any required skill files
3. Calls the Anthropic API with the context object and prompt
4. Validates the returned context object structure before passing it forward
5. Appends a one-line entry to run_log on completion

### After the pipeline runs
1. Check outputs/ for the completed article draft
2. Check logs/ for the run log
3. Review the qa_notes field for the QA report and final recommendation
4. Action any founder review requirements before editing the article
5. Complete human review and log any edits as prompt improvements

## Standing rules that apply to every agent
- UK English throughout — spellings, idioms, and references must be British
- No em dashes under any circumstances
- No corporate jargon
- No three-sentence AI pattern
- Write for fleet operators, not marketers
- Every agent must read the shared context object before doing its job
- Every agent must validate the context object structure before passing it forward
- Never fabricate research findings, sources, or data points
- Flag missing information explicitly rather than guessing

## Tools and integrations
- Anthropic API — claude-sonnet-4-6 — all agent calls
- Serper.dev — Google search for the research agent
- Apify — Reddit scraper for the research agent
- n8n — pipeline orchestration
- Notion — brief storage and article output destination

## Pending
- brand-pov.md topics and positions to avoid section — requires additional founder input
- n8n workflow configuration — to be built once all prompt and skill files are complete
- First test run — to be run against a real brief once API keys are authenticated

## Improvement protocol
After every human review, log every edit made to the article and identify which agent produced the content that needed changing. Use this to improve the relevant prompt or skill file. The pipeline compounds in quality over time if every human edit is treated as a prompt fix.
