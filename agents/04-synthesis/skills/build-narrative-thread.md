# Skill: Build Narrative Thread

## Purpose
Construct the narrative thread for the full article after all sections have been individually synthesised. The narrative thread is not a summary of the article — it is the story logic that connects every section into a coherent whole. It tells the writing agent what the article is ultimately arguing, how each section advances that argument, what role each section plays in the overall story, and what the reader should think, feel, and do by the end.

## When to apply this skill
Apply once, after extract-key-points.md has been completed for every section. This is the final skill in the synthesis stage and operates at article level, not section level.

## What this skill produces
A narrative_thread field to be populated in the context object at the top level. The narrative thread must be detailed enough that the writing agent can read it once and understand the full story arc of the article before writing a single word.

---

## How to build the narrative thread

### Step 1 — Read the full picture
Before writing anything, read and hold in working memory:
- article_goal — what this article needs to achieve
- traknova_pov — how Traknova wants to position itself on this topic
- All ICP profiles listed in icp_profile — specifically conversion_goal, what_they_care_about, and beliefs_to_align_with
- Every section heading in order
- The lead argument key point from every section — these are the backbone of the article's argument

### Step 2 — Identify the central argument
The central argument is the single most important thing the article is trying to convince the reader of. It is not the topic of the article — it is the position the article takes on that topic.

To identify it, ask:
- What does the reader believe at the start of this article that we want them to think differently about by the end?
- What does Traknova want the reader to understand or conclude that they would not have concluded without reading this article?
- If the reader reads only the lead argument key points from each section in order, what argument do they add up to?

Write the central argument as a single clear statement. It can be as long as it needs to be to be precise and complete — do not compress it into a tagline.

### Step 3 — Map each section to its role in the story
Every section plays a specific role in advancing the central argument. Assign each section one of the following narrative roles and write one to two sentences explaining how this section advances the story:

- establish the problem — opens the article by making the reader feel the pain or challenge the article addresses. Should make the reader think "yes, this is exactly my situation."
- deepen the problem — adds dimension to the problem established in the opening. Shows why it is more serious, more costly, or more urgent than the reader may have realised.
- introduce the turning point — shifts the article from problem to possibility. Introduces the idea that the problem is solvable and that others have solved it.
- build the case — provides the evidence, examples, and argument that the solution works. This is the core of the article's persuasive work.
- address the doubt — acknowledges the reader's scepticism or the most common objection and resolves it credibly.
- show the outcome — makes the solution concrete by describing what changes for the reader if they act. Connects back to the ICP's conversion_goal.
- close and direct — brings the article to a conclusion and gives the reader a clear next step or takeaway. Should not feel like a sales pitch — it should feel like the natural conclusion of the argument.

Not every article will have all seven roles. Some roles may be covered across multiple sections. Some sections may serve a combined role. The mapping must reflect the actual sections in this article, not an idealised structure.

### Step 4 — Write the opening and closing intent
Describe in specific terms:

- Opening intent: what the first section must establish in the reader's mind. What should the reader be thinking and feeling after the first section? What tone does it set for the rest of the article?
- Closing intent: what the final section must leave the reader with. What is the last thought or feeling the article produces? How does it connect to the ICP's conversion_goal without reading as a hard sell?

### Step 5 — Write transition logic between sections
For each pair of adjacent sections, write one sentence describing how the article moves from the first section to the second. This is the connective tissue of the article — the writing agent uses this to write transitions that feel natural rather than abrupt.

Format as:
- Section 1 → Section 2: [transition logic]
- Section 2 → Section 3: [transition logic]
- And so on for every adjacent pair

### Step 6 — Write the narrative thread
Combine Steps 2 through 5 into a single cohesive narrative thread document. Structure it as follows:

1. Central argument
2. Section map with narrative roles
3. Opening intent
4. Closing intent
5. Transition logic

The narrative thread should be written as instructions to the writing agent — direct, specific, and actionable. Every sentence should tell the writing agent something it needs to know to write the article well.

---

## Rules
- The central argument must be derived from the article_goal and the key points — do not invent a new argument
- Every section in the sections array must appear in the section map — do not skip sections
- Transition logic must be specific to adjacent sections — do not write generic transitions like "then the article moves to the next topic"
- The closing intent must connect explicitly to the ICP's conversion_goal — the article should move the reader toward the action Traknova wants them to take
- Do not write the narrative thread as a summary of what each section contains — write it as a description of what each section does to the reader and to the argument
- The narrative thread must be detailed enough that a writer who has not read the brief or the research could understand the full shape of the article from this document alone

## Example output structure

CENTRAL ARGUMENT
PCO drivers are paying more for insurance than their risk profile justifies, and the gap between what they pay and what they should pay is closed by data — specifically the kind of data that a properly installed tracking and dash cam system captures automatically. The article argues that fleet security technology is not a cost for PCO operators, it is a commercial lever, and that the operators who understand this are already using it to their advantage at renewal.

SECTION MAP
Section 1 — Why PCO drivers pay more for insurance than standard car owners
Narrative role: establish the problem
This section makes the reader feel the unfairness of their current situation and validates that the premium gap is real and documented, not just their perception.

Section 2 — What insurers are actually looking at when they price a PCO policy
Narrative role: deepen the problem
This section reframes the problem — it is not arbitrary, it is based on data signals, and most PCO drivers are sending the wrong signals without knowing it.

Section 3 — How tracking data changes what the insurer sees
Narrative role: introduce the turning point
This section introduces the idea that the data already exists to change the insurer's picture of the driver — the driver just needs to capture and present it.

Section 4 — What operators who have done this are seeing at renewal
Narrative role: build the case
This section makes the argument concrete with real outcomes from UK operators who have used telematics data in insurance conversations.

Section 5 — The objection: does this actually work or is it a sales claim
Narrative role: address the doubt
This section validates the reader's scepticism and resolves it with third party evidence rather than Traknova claims.

Section 6 — What changes when you have the right system in place
Narrative role: show the outcome
This section describes the day-to-day and renewal-time difference for a PCO driver who has made the switch.

OPENING INTENT
The first section must make the PCO driver reader feel immediately understood. The tone is peer-level — not a brand explaining a problem to a customer, but one operator acknowledging a reality that another operator already lives with. By the end of the first section the reader should be thinking: this article gets my situation.

CLOSING INTENT
The final section should leave the reader with a clear picture of what their situation looks like after acting — not a list of product features, but a description of the commercial and operational difference. The last thought should be: I should find out what this would look like for my vehicle. This connects directly to the PCO Operator conversion_goal of taking one next step toward a consultation or enquiry.

TRANSITION LOGIC
Section 1 → Section 2: Having established that PCO drivers pay more, the article shifts from the experience of the problem to the mechanism behind it — moving the reader from frustration to understanding.
Section 2 → Section 3: Having explained what insurers look at, the article introduces the idea that those signals can be changed — shifting from diagnosis to possibility.
Section 3 → Section 4: Having introduced the possibility, the article grounds it in real UK outcomes — shifting from theory to evidence.
Section 4 → Section 5: Having presented the evidence, the article anticipates the reader's doubt and addresses it directly — this is the credibility-building move.
Section 5 → Section 6: Having resolved the doubt, the article moves to the outcome — what the reader's situation looks like on the other side of the decision.
