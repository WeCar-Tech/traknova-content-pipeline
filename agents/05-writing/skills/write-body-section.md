# Skill: Write Body Section

## Purpose
Write each body section of the article using the key points produced by the synthesis agent, the narrative thread, and the rolling context of what has already been written. Body sections are the core of the article's persuasive and informational work. Each one must advance the central argument, add something the previous section did not, speak directly to the target ICP, and be structured for search engine and LLM visibility.

## When to apply this skill
Apply to every section that is not section 1 and not the final section, as part of the writing agent's Step 3.

## What this skill produces
A completed body section populated in the section's draft field.

---

## How to write each body section

### Step 1 — Read before writing
Before writing this section, read and hold in working memory:
- The section's key_points array — specifically the point assigned how_to_use "lead argument"
- The narrative role assigned to this section in narrative_thread
- The transition logic for the previous section to this section from narrative_thread
- full_draft_so_far — check what has already been said and what tone has been established
- The icp_angle and traknova_angle for each key point — these are instructions for how to frame each point

### Step 2 — Write the opening sentence
The opening sentence of every body section must do two things simultaneously: connect to what came before and signal what this section is about.

Use the transition logic from narrative_thread to inform the connection. Do not write a transition that summarises the previous section — move forward, do not look back.

The opening sentence must:
- Not restate the section heading
- Not open with "In this section" or any meta-reference to the article structure
- Not use the three-sentence AI pattern
- Contain a concrete element — a specific reference to the ICP's world, a named situation, or a direct statement of the section's lead argument
- Flow naturally from the last sentence of the previous section

### Step 3 — Develop the lead argument
Find the key point with how_to_use "lead argument" and build the first substantive paragraph around it. This paragraph must:
- State the lead argument clearly and specifically within the first two to three sentences of the section
- Use the icp_angle to frame the argument for the target reader — write so the reader recognises their own situation in what is being said
- Use the traknova_angle to connect the argument to Traknova's position — do this through substance, not by mentioning Traknova by name unless the brief specifically requires it
- Cite the source_reference if the key point is drawn from a specific source — integrate the reference naturally, not as a footnote or parenthetical

### Step 4 — Build with supporting points
After establishing the lead argument, develop the section using the remaining key points in the order that makes the most logical sense. Apply the following rules for each how_to_use type:

- supporting evidence — use this to reinforce the lead argument with a second data point, a different source type, or a UK-specific dimension. Do not introduce supporting evidence before the lead argument is established.
- example — use this to make the argument concrete. Introduce the example after the lead argument and at least one piece of supporting evidence. Frame it in terms the ICP would immediately recognise — a situation they have been in, heard about, or could imagine happening to them.
- counter and resolve — use this to acknowledge the reader's most likely objection to the section's argument. Introduce it as a genuine concern, not a strawman. Resolve it with evidence or reasoning, not with reassurance. The resolution must be more persuasive than the objection.
- transition — use this as the closing point of the section. It should close the section's argument and create a natural lead into the next section without summarising what just happened.

### Step 5 — Apply search and LLM visibility rules
Before finalising the section, check the following:

- Answer the section's core question directly and early — the question implied by the section heading must be answered within the first two to three sentences. Do not make the reader work to find the answer.
- Include at least one directly quotable or citable sentence — a specific claim, statistic, or insight stated with enough precision that it could be lifted and cited by an LLM or linked to by another publication. This sentence should stand on its own as a complete, useful answer to a specific question.
- Use semantic variations of the primary keyword naturally — do not repeat the exact phrase from the headline. Use related terms and the language the ICP uses when discussing this topic.
- Use precise language throughout — "operators with hardwired GPS trackers reported fewer at-fault insurance claims" is citable. "Tracking helps with insurance" is not.
- Structure the section so it can stand alone as a useful answer — a reader or LLM encountering only this section should be able to extract a complete, useful answer to the question the heading implies.
- Write with E-E-A-T signals — cite sources, reference real situations, take a clear position, write with the authority of someone who understands this industry from the inside.

### Step 6 — Close the section
The final sentence of every body section must do one of the following:
- Set up the next section using the transition logic from narrative_thread — move the reader forward without announcing that you are doing so
- Land the section's argument with a specific, concrete statement that the reader will remember — not a summary, a conclusion
- Pre-empt a question the reader is likely asking after reading this section — one that the next section will answer

Do not close a body section with:
- A summary of what the section just said
- A vague forward reference like "we will explore this further in the next section"
- A call to action — that belongs in the conclusion only
- An em dash

---

## Length
Each body section should be between 150 and 350 words depending on the complexity of the key points. Sections making a data-backed argument typically need more space. Sections illustrating with an example can be tighter. Do not pad to hit a word count. Do not cut a point short to stay under it.

If the brief specifies a word count per section, follow it.

---

## Rules
- Every body section must contain at least one specific, concrete detail — a number, a named situation, a real outcome, or a direct reference to the ICP's world
- Do not repeat an argument, fact, or example that has already appeared in full_draft_so_far
- Do not use em dashes
- Do not use the three-sentence AI pattern
- Do not use corporate jargon
- Do not write in bullet points unless presenting three or more discrete items where prose would be harder to read
- Do not open with the section heading restated as a sentence
- Do not open consecutive sections with the same sentence structure — vary the opening across sections
- Write in UK English throughout
- Every key point in the section's key_points array must be addressed — do not drop a key point because it is difficult to integrate

---

## Example

Section heading: What insurers are actually looking at when they price a PCO policy
Narrative role: deepen the problem
Lead argument key point: Insurance premiums for PCO drivers are not arbitrary — they are calculated from specific risk signals, most of which drivers are sending without knowing it.

"The price on your renewal letter is not a guess. Insurers pricing PCO policies are working from a set of risk signals — claims history, vehicle type, hours of operation, geographic area, and increasingly, whether you have any data to counter their assumptions about how you drive and where.

The problem for most private hire operators is that the default signals work against them. Without telematics data, an insurer has no way to distinguish a careful driver with ten years of PCO experience from someone who has just started. Both get priced on category averages, and those averages are pulled up by the worst performers in the pool.

A 2024 report from the BVRLA found that fleets using telematics data in renewal conversations achieved an average 12% reduction in premiums compared to non-telematics fleets of equivalent size. The mechanism is straightforward: data changes what the insurer sees. It moves the conversation from assumption to evidence.

For PCO operators, this means the question is not whether tracking affects your premium. It is whether you are capturing the right data and presenting it at the right moment."
