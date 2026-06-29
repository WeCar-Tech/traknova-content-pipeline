# Skill: Storytelling

## Purpose
This skill is a quality check applied to every section after it has been drafted. It does not rewrite the section from scratch — it identifies specific weaknesses in the draft that reduce its narrative quality, ICP resonance, and LLM citability, and provides targeted instructions for fixing them before the section is finalised.

A section can be factually accurate, well-structured, and ICP-relevant but still read like a report rather than a story. This skill catches that. The difference between a section that gets read and shared and one that gets skimmed and forgotten is almost always a storytelling problem — not a research problem.

## When to apply this skill
Apply to every section after the relevant writing skill (write-introduction, write-body-section, or write-conclusion) has produced a draft, and before the section is finalised and appended to full_draft_so_far.

## What this skill produces
Either a confirmation that the section passes all checks and is ready to finalise, or a list of specific targeted fixes with rewritten sentences or paragraphs where needed. Do not produce vague feedback — every issue identified must come with a specific fix.

---

## The checks

### Check 1 — Specificity
Read every sentence in the section. Flag any sentence that makes a claim without a concrete detail to support it.

The em dash character is: —. Flag every single instance of this character without exception. Also flag -- used as a substitute for an em dash.

A sentence fails this check if it:
- Makes a general statement about a trend, problem, or outcome without a specific number, named situation, or real example
- Could have been written without any research — it contains no information that required finding
- Uses vague intensifiers: "significantly", "dramatically", "greatly", "considerably", "many operators", "most fleets"

A sentence passes this check if it:
- Contains a specific number, percentage, timeframe, or named source
- References a situation the target ICP would recognise from their own experience
- Makes a claim precise enough that it could be fact-checked

Fix: replace vague claims with the specific detail from the key points or source_reference. If no specific detail exists for this claim, remove the sentence rather than leaving it vague.

---

### Check 2 — The AI pattern
Read the section looking for the three-sentence AI pattern: broad statement, slightly more specific statement, conclusion that restates the first sentence.

Examples of the pattern to catch:
- "Fleet security is important for any operator. Managing a fleet comes with significant risks. That is why having the right security measures in place matters."
- "Insurance costs are a major concern for PCO drivers. Many operators find premiums difficult to manage. Understanding what drives these costs is the first step."
- "Tracking technology has changed significantly in recent years. Modern systems offer capabilities that were not available before. This means operators now have more options than ever."

If this pattern appears anywhere in the section, rewrite the affected sentences. The fix is always to collapse the three sentences into one precise, specific sentence that says what the three were circling around.

Fix example:
Before: "Insurance costs are a major concern for PCO drivers. Many operators find premiums difficult to manage. Understanding what drives these costs is the first step."
After: "PCO drivers in London pay an average of 40% more for commercial vehicle insurance than equivalent private drivers — and most have no clear picture of what is driving that gap."

---

### Check 3 — ICP voice
Read the section and check whether it sounds like it was written for this specific ICP or for a generic fleet industry audience.

Flag any sentence or paragraph that:
- Uses language the ICP would not use or recognise — draw from language_and_tone.avoid in the ICP profile
- Describes the ICP's situation from the outside rather than from inside their experience
- Uses job title language or corporate framing when the ICP is an owner-operator
- Misses an opportunity to use a term, reference, or situation specific to this ICP's world

Check: would this sentence make a PCO driver, taxi company owner, or fleet manager think "this is written for someone like me" — or would they feel like they are reading content aimed at a different audience?

Fix: rewrite flagged sentences using the language_and_tone.use field from the ICP profile. Replace generic fleet references with ICP-specific ones. Replace corporate framing with operator framing.

---

### Check 4 — Show, do not label
Read the section for adjectives and descriptors that make claims about Traknova or its approach without demonstrating them.

Flag any instance of:
- "innovative", "industry-leading", "best-in-class", "powerful", "advanced", "sophisticated"
- "seamless", "easy", "simple", "straightforward" — unless followed immediately by a specific demonstration of why
- Any sentence that describes Traknova's approach as something positive without showing what that means in practice

Fix: remove the label and replace it with the specific thing it was trying to claim. "Traknova's innovative approach" means nothing. "Traknova's digital tracking layer reads data already built into vehicles from 2016 onwards, removing the need for hardware installation" shows innovation without labelling it.

---

### Check 5 — Narrative momentum
Read the section as a whole and check whether it advances the article's central argument or merely occupies space.

Ask:
- What does the reader know or believe after reading this section that they did not know or believe before?
- Does this section move the article's argument forward or does it tread water?
- Does the final sentence of this section create a reason to read the next section?

A section fails this check if:
- It restates information already covered in full_draft_so_far without adding a new dimension
- It ends on a weak or generic sentence that does not set up what follows
- The reader could skip this section without losing the thread of the article's argument

Fix: identify the one thing this section must add to the article that no other section adds. If the section is not adding that thing clearly, restructure around it. If the section is duplicating another section, flag it for the human reviewer.

---

### Check 6 — LLM citability
Read the section and identify whether it contains at least one sentence that is precise, self-contained, and specific enough to be cited by an LLM as an answer to a question.

A citable sentence:
- States a specific claim, statistic, or position with enough precision to stand alone
- Does not require the surrounding context to make sense
- Is written in active voice
- Contains no hedging language: "may", "might", "could potentially", "in some cases"

A non-citable sentence:
- "Tracking can help fleet operators manage their insurance costs more effectively."
- "Many PCO drivers have found that having a dash cam provides peace of mind."
- "Fleet management technology has become increasingly important in recent years."

If the section contains no citable sentence, identify the strongest claim in the section and rewrite it to be precise, active, and self-contained.

---

## How to report findings

If all six checks pass: return "storytelling check passed — section ready to finalise."

If any check fails: return a structured list in the following format:

CHECK [number] — [check name]: FAIL
Issue: [one sentence describing the specific problem]
Location: [quote the specific sentence or sentences that fail]
Fix: [the rewritten sentence or sentences that resolve the issue]

Apply all fixes before the section is appended to full_draft_so_far. Do not finalise a section with outstanding storytelling failures.

---

## Rules
- Do not rewrite the entire section — fix only what fails a check
- Do not introduce new information or key points during storytelling fixes — only improve what is already there
- Do not soften fixes to preserve the original draft — if a sentence fails a check, fix it precisely
- Apply all six checks to every section without exception — do not skip checks for sections that seem strong
- If a fix requires information that does not exist in the key_points or filtered_findings, flag it rather than inventing detail
