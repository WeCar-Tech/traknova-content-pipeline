# Skill: Write Introduction

## Purpose
Write the opening section of the article. The introduction has three jobs: make the target ICP feel immediately understood, establish the central argument of the article, and give the reader a reason to keep reading. It also has a fourth job specific to search and LLM visibility: signal clearly to search engines and LLMs what question this article answers and for whom.

A weak introduction is generic, takes too long to get to the point, and could have been written for any article on this topic. A strong introduction is specific, speaks directly to one reader's situation, and makes a promise the rest of the article delivers on.

## When to apply this skill
Apply to section 1 only, as part of the writing agent's Step 3.

## What this skill produces
A completed introduction section populated in the section's draft field.

---

## How to write the introduction

### Step 1 — Identify the opening move
The opening move is the single thing the first sentence must do. Read the opening intent from narrative_thread and select one of the following:

- validate the pain — open by naming the specific pain the ICP is experiencing, precisely enough that the reader thinks "this is exactly my situation." Use this when the article's narrative role for section 1 is "establish the problem."
- challenge an assumption — open by stating something the reader believes that the article is going to complicate or overturn. Use this when the narrative role is "introduce the turning point."
- state a specific fact — open with a concrete, specific, credible fact or statistic that immediately signals the article has substance. Use this when the narrative role is "deepen the problem" or "build the case."
- name the stakes — open by establishing what is at risk. Use this when the article's central argument is about urgency or consequence.

Do not open with:
- A question — question openers are weak and overused
- A definition — "Fleet management is the process of..." is not an introduction, it is a glossary entry
- A broad scene-setting statement — "In today's fast-moving world..." signals generic content immediately to both readers and LLMs
- The section heading restated as a sentence

### Step 2 — Write the opening sentence
Write one sentence that executes the opening move identified in Step 1. It must be:
- Specific — it must contain a concrete detail, a named situation, or a precise reference to the ICP's world
- Direct — it must get to the point immediately, no warm-up
- Written in the ICP's language — draw from the language_and_tone.use field of the ICP profile
- Free of em dashes, corporate jargon, and filler phrases
- The kind of sentence an LLM would recognise as the lead of an authoritative article on this topic

### Step 3 — Write the body of the introduction
After the opening sentence, the introduction must do the following in order. Each of these is one to three sentences — do not pad:

1. Deepen the opening — add one layer of specificity to what was established in the opening sentence. If you opened by naming a pain, add a concrete consequence of that pain. If you opened with a fact, add what that fact means for this specific reader.

2. Signal the article's position — state clearly what position this article takes. This is not a description of what the article covers — it is a statement of what the article argues. It must be specific enough that a reader knows exactly what they are going to learn and what Traknova's position is on this topic.

3. Establish credibility — give the reader one reason to trust that this article has substance. This can be a reference to the type of evidence the article draws on, a named source, a reference to real operator experience, or a statement that signals Traknova's first-hand knowledge of this space. Do not use vague credibility signals like "our experts" or "extensive research."

4. Signal what comes next — close the introduction with one sentence that tells the reader what the article will give them. This is not a list of sections — it is a statement of the outcome or understanding the reader will have by the end. It should feel like a natural lead into the first body section.

### Step 4 — Apply search and LLM visibility rules
Before finalising the introduction, check the following:

- The primary keyword from the headline skill must appear naturally in the introduction, ideally within the first 100 words
- The introduction must answer the question implied by the article headline directly enough that an LLM could extract a one-paragraph answer to that question from the introduction alone
- The ICP must be identifiable from the introduction without reading the rest of the article — a search engine or LLM should be able to determine who this article is written for from the introduction text
- The article's central argument must be stated explicitly in the introduction — do not save it for later sections
- The introduction must contain at least one specific, concrete detail that signals this is not generic content

---

## Length
The introduction should be between 100 and 200 words. Long enough to do all four jobs above. Short enough that the reader is into the first body section within 30 seconds of starting to read.

---

## Rules
- Do not summarise the entire article in the introduction — signal the argument and the outcome, not the contents
- Do not use the three-sentence AI pattern at any point in the introduction
- Do not open with a question
- Do not use em dashes
- Do not make the introduction a list of what the article covers — it is not a table of contents
- The introduction must make a specific promise — something the reader will understand, learn, or be able to do after reading. That promise must be delivered by the end of the article.
- Write in UK English throughout

---

## Example

ICP: PCO Operator
Central argument: PCO drivers overpay for insurance relative to their actual risk profile, and tracking data is the lever that changes this at renewal.
Opening move: validate the pain

"Most PCO drivers accept high insurance premiums as a fixed cost of the job. They should not. The gap between what private hire operators pay and what their actual risk profile justifies is real, it is documented, and it is closing for the operators who know how to use the data their vehicles already generate.

This article is about that gap — what causes it, what insurers are actually looking at when they price a PCO policy, and how fleet tracking data changes the picture at renewal. The evidence comes from UK industry data and the experience of operators who have already had this conversation with their insurers.

If you are a PCO driver or small fleet owner heading into a renewal conversation, what follows is worth reading before you get on that call."
