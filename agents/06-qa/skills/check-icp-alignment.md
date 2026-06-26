# Skill: Check ICP Alignment

## Purpose
Assess whether the article consistently speaks to the right reader in the right way throughout. ICP alignment problems occur when the article drifts toward generic fleet industry content, uses language or references that belong to a different ICP, or fails to connect its arguments to the specific pains, beliefs, and conversion goal of the target reader. An article can be well-written and factually sound but still fail to resonate with the target ICP if the alignment is off.

## When to apply this skill
Apply to the full draft as part of the QA agent's Step 3. Read the entire article before identifying alignment issues — alignment problems are often cumulative, building across sections rather than appearing in one place.

## What this skill produces
A structured list of ICP alignment findings, each with a location, severity, and recommended fix. If no alignment issues are found, return "check-icp-alignment: no issues found."

---

## Before running checks
Load and hold in working memory for every ICP listed in icp_profile:
- who_they_are
- what_they_care_about
- core_pains_to_address
- beliefs_to_align_with
- objections_to_pre-empt
- language_and_tone — both use and avoid lists
- conversion_goal

---

## The checks

### Check 1 — Reader identification
Read the full draft and assess whether the target ICP is identifiable from the article alone — without reading the brief or the context object.

Flag if:
- The article could have been written for a different ICP without changing more than a few words
- The introduction does not signal who the article is written for within the first two sentences
- The article uses generic fleet industry language throughout rather than ICP-specific language
- The target reader's role, fleet size, or specific context is never referenced concretely

For multi-ICP articles: flag if any ICP listed in icp_profile is not addressed at any point in the article. Every target ICP must be spoken to at least once, even if one is primary.

Severity guide:
- ICP is identifiable but references are sparse — minor
- ICP is only identifiable from the topic, not from the language or framing — moderate
- Article is written for a generic fleet audience with no ICP-specific signals — major

---

### Check 2 — Pain alignment
Read the full draft and assess whether the article addresses the core pains listed in the ICP profile's core_pains_to_address.

For each pain listed in core_pains_to_address that is relevant to this article's topic, check whether it is addressed somewhere in the draft. It does not need to be named explicitly — it can be addressed through an example, a statistic, or a scenario that the ICP would recognise as their own experience.

Flag if:
- A core pain directly relevant to the article's topic is not addressed anywhere in the draft
- A core pain is mentioned but described from the outside rather than from the ICP's perspective — the reader would not feel understood, only observed
- The article addresses a pain that is not in core_pains_to_address while missing one that is

Severity guide:
- A relevant pain is addressed but lightly — minor
- A directly relevant pain is not addressed at all — moderate
- The article addresses pains belonging to a different ICP — major

---

### Check 3 — Belief alignment
Read the full draft and assess whether the article reinforces the beliefs listed in the ICP profile's beliefs_to_align_with.

These beliefs are the existing convictions the target reader holds that the article should strengthen and build on. The article should not contradict them, undermine them, or ignore them.

Flag if:
- The article contradicts a stated belief — for example, arguing that fleet technology is complex and difficult to implement when the ICP believes technology should make running a fleet simpler
- A key belief is relevant to the article's topic but is not reinforced anywhere in the draft
- The article takes a neutral position on something the ICP has a strong belief about — neutrality on a belief the reader holds reads as disagreement

Severity guide:
- A relevant belief is not reinforced but is not contradicted — minor
- A relevant belief is contradicted — major
- The article is neutral throughout with no alignment to any stated belief — moderate

---

### Check 4 — Objection handling
Read the full draft and assess whether the article addresses the objections listed in the ICP profile's objections_to_pre-empt that are relevant to this article's topic.

Flag if:
- A directly relevant objection is not addressed anywhere in the draft
- An objection is raised but not resolved — the article acknowledges the concern and moves on without a credible resolution
- The resolution of an objection relies on reassurance rather than evidence — "you can trust that this works" is not a resolution
- An objection is resolved too early in the article before enough credibility has been established for the resolution to land

Severity guide:
- A relevant objection is addressed but the resolution is weak — minor
- A directly relevant objection is not addressed at all — moderate
- A major objection is raised and left unresolved — major

---

### Check 5 — Language alignment
Read the full draft and flag any language that appears in the ICP profile's language_and_tone.avoid list, and any missed opportunity to use language from the language_and_tone.use list.

Flag if:
- Any term, phrase, or framing from language_and_tone.avoid appears in the draft
- The article consistently misses opportunities to use ICP-specific language from language_and_tone.use — for example, writing "vehicle tracking" throughout when the PCO Operator profile specifies using "TfL", "PCO licence", and "relay theft" as specific references
- The article uses terminology that belongs to a different ICP — for example, using "tachograph" language in an article written for PCO operators rather than logistics fleet managers

Severity guide:
- One or two instances of avoided language — minor
- Consistent use of avoided language throughout — moderate
- Article uses the language profile of the wrong ICP — major

---

### Check 6 — Conversion goal alignment
Read the conclusion and assess whether it connects to the ICP's conversion_goal.

The conversion_goal describes the specific action or next step the article should move the reader toward. The conclusion must be written so that the reader's natural response is to take that step.

Flag if:
- The conclusion ends with a generic call to action that does not reflect the specific conversion_goal
- The conclusion asks the reader to do something more demanding than the conversion_goal specifies — for example, asking for a purchase decision when the conversion_goal is a consultation
- The conclusion does not give the reader a clear next step at all
- The next step in the conclusion is framed in terms of what Traknova offers rather than what the reader gets

Severity guide:
- Next step is present but not framed around the reader's gain — minor
- Next step does not match the conversion_goal — moderate
- No next step in the conclusion — major

---

## Output format

For each issue found:

ICP ALIGNMENT — CHECK [number] — [check name]
Location: [section heading or quoted sentence]
Issue: [one sentence describing the specific problem]
Severity: [minor / moderate / major]
Recommended fix: [specific instruction — what needs to change and how]

If no issues found for a check: ICP ALIGNMENT — CHECK [number] — [check name]: no issues found.
