# Skill: Check Flow

## Purpose
Assess whether the article reads as a coherent, continuously advancing piece of writing from start to finish. Flow problems are the most common reason a well-researched article fails to hold the reader's attention. They include abrupt transitions, sections that repeat rather than advance, structural logic that is hard to follow, and an opening or closing that does not do its job.

## When to apply this skill
Apply to the full draft as part of the QA agent's Step 3. Read the entire article before identifying any flow issues — do not assess sections in isolation.

## What this skill produces
A structured list of flow findings, each with a location, severity, and recommended fix. If no flow issues are found, return "check-flow: no issues found."

---

## The checks

### Check 1 — Opening effectiveness
Read the introduction. Assess whether it executes the opening intent from narrative_thread.

Flag if:
- The introduction does not make the target ICP feel immediately addressed within the first two sentences
- The central argument is not signalled clearly in the introduction
- The introduction summarises the article's contents rather than establishing its argument
- The introduction opens with a question, a definition, or a broad scene-setting statement
- The introduction does not create a clear reason to read on

Severity guide:
- Introduction signals the argument but slowly — minor
- Introduction does not signal the argument at all — major
- Introduction opens with a question or definition — moderate

---

### Check 2 — Section transitions
Read the final sentence of each section and the opening sentence of the following section. Assess whether the transition between them is smooth and purposeful.

Flag if:
- The opening sentence of a section does not connect to what came before
- The transition announces itself — "In the next section we will look at..." or "Now that we have covered X, let us turn to Y"
- The final sentence of a section and the opening sentence of the next section cover the same ground
- There is a jarring tonal or logical shift between sections with no bridge

For each flagged transition, identify the two sections involved.

Severity guide:
- Transition is abrupt but the logical connection is clear — minor
- Transition is absent and the logical connection is unclear — moderate
- Transition creates a contradiction or logical gap — major

---

### Check 3 — Argument progression
Read the section map from narrative_thread. Then read the full draft and assess whether each section advances the article's central argument in the way its narrative role requires.

Flag if:
- A section assigned "establish the problem" does not make the reader feel the problem — it describes it from a distance
- A section assigned "build the case" does not contain specific evidence — it makes assertions without support
- A section assigned "address the doubt" raises the objection but does not resolve it convincingly
- A section assigned "show the outcome" stays abstract rather than making the outcome concrete
- Any section repeats the central argument of a previous section without adding a new dimension
- Any section could be removed without weakening the article's overall argument

Severity guide:
- Section partially fulfils its narrative role — minor
- Section does not fulfil its narrative role — moderate
- Section undermines the argument of a previous section — major

---

### Check 4 — Repetition
Read the full draft looking for arguments, facts, examples, or phrases that appear more than once.

Flag if:
- The same statistic or data point is cited in more than one section
- The same example or operator scenario is referenced more than once
- The same core argument is made in similar language across two or more sections
- A phrase or sentence construction appears verbatim or near-verbatim in multiple sections

Severity guide:
- Minor variation in repeated content — minor
- Identical argument made in two sections — moderate
- Identical sentence or phrase appearing multiple times — major

---

### Check 5 — Closing effectiveness
Read the conclusion. Assess whether it executes the closing intent from narrative_thread and connects to the ICP's conversion_goal.

Flag if:
- The conclusion summarises the article rather than landing its argument
- The conclusion introduces new information not established earlier in the article
- The conclusion ends with a generic call to action disconnected from the article's argument
- The conclusion does not give the reader a specific, low-friction next step
- The conclusion does not connect to the ICP's conversion_goal

Severity guide:
- Conclusion lands the argument but next step is weak — minor
- Conclusion summarises rather than lands — moderate
- Conclusion does not connect to conversion goal at all — major

---

## Output format

For each issue found:

FLOW — CHECK [number] — [check name]
Location: [section heading or quoted sentence]
Issue: [one sentence describing the specific problem]
Severity: [minor / moderate / major]
Recommended fix: [specific instruction — what needs to change and how]

If no issues found for a check: FLOW — CHECK [number] — [check name]: no issues found.
