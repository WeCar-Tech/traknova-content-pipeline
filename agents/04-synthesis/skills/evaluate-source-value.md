# Skill: Evaluate Source Value

## Purpose
Determine how each filtered finding should be used by the writing agent. A finding is not just a piece of information — it can serve different roles in an article depending on its content, credibility, and relationship to the section's argument. This skill assigns each finding a usage role so the writing agent knows exactly what to do with it.

## When to apply this skill
Apply to every finding in filtered_findings for each section as part of the synthesis agent's Step 2. This is the first of two skills applied at finding level before extract-key-points is run.

## What to add to each finding object
Append the following fields:

- usage_role: one of the roles defined below
- usage_notes: one to three sentences explaining how the writing agent should use this finding — be specific about what the finding contributes to the section and how it should be positioned for the target ICP

---

## Usage roles

### primary_claim
The finding contains a specific, credible, ICP-relevant fact, statistic, or conclusion that the section should be built around. A section should have no more than one primary_claim finding. If multiple findings could serve as primary_claim, select the one with the highest combined credibility_score and icp_relevance_score.

Use when:
- The finding contains a named statistic or data point from a credible source
- The finding is the strongest evidence for the section's main argument
- The finding is specific enough that it anchors the section's core point

### supporting_evidence
The finding corroborates, reinforces, or adds depth to the primary claim. It does not stand alone as the centrepiece but makes the primary claim more convincing.

Use when:
- The finding provides a second data point or perspective that backs up the primary claim
- The finding comes from a different source type than the primary claim, adding breadth
- The finding adds a UK-specific, ICP-specific, or industry-specific dimension to the primary claim

### real_world_example
The finding describes a specific situation, case, or experience that illustrates the section's argument in concrete terms. Examples make abstract arguments tangible for the reader.

Use when:
- The finding describes what happened to a real operator, fleet, or business
- The finding is a forum post or community discussion where an operator describes their experience
- The finding contains a named case study or outcome

### counter_and_resolve
The finding presents a perspective, objection, or challenge that contradicts or complicates the section's argument. Rather than filtering this out, the writing agent should acknowledge it and resolve it — this builds credibility with a sceptical ICP reader.

Use when:
- The finding reflects a common objection listed in the ICP profile's objections_to_pre-empt
- The finding presents a genuine challenge or limitation that the target reader would already be aware of
- The finding has pov_conflict_status "caution" but contains a real operator concern worth addressing

### background_context
The finding provides useful context that helps frame the section but is not strong enough to serve as a primary claim or supporting evidence on its own. Use sparingly — the writing agent should not lean on background context as a substitute for evidence.

Use when:
- The finding provides definitional or explanatory information the reader may need
- The finding establishes the scale or scope of a problem without providing specific data
- The finding is older or less credible but still useful for framing

### do_not_use
The finding was passed through analysis but on closer review at synthesis stage provides no clear value for this specific section. It should not be referenced in the draft.

Use when:
- The finding duplicates a stronger finding already assigned a usage role
- The finding is too tangential to contribute meaningfully to the section
- The finding has a caution note that makes it too risky to use even with care

---

## Rules
- Every finding in filtered_findings must receive a usage_role — do not leave any finding unassigned
- A section should have no more than one primary_claim finding
- Do not assign real_world_example to a finding that describes a general trend rather than a specific situation
- Do not assign counter_and_resolve unless the finding genuinely reflects a concern the ICP would have — not every challenge is worth raising
- usage_notes must be specific to this section and this ICP — do not write generic notes that could apply to any article
- A finding assigned do_not_use does not need detailed usage_notes — a single sentence explaining why it is not being used is sufficient

---

## Example outputs

### primary_claim
```json
{
  "usage_role": "primary_claim",
  "usage_notes": "Use this BVRLA statistic as the anchor for the section — fleets with telematics reported 12% average insurance reduction at renewal. Lead with this figure to establish the financial case immediately. Frame it for the PCO Operator as proof that tracking data has a direct and measurable impact on what they pay at renewal, not just a vague benefit."
}
```

### counter_and_resolve
```json
{
  "usage_role": "counter_and_resolve",
  "usage_notes": "This Reddit post reflects a PCO driver who tried an OBD tracker and found it was removed by a thief easily. This maps directly to the objection 'Is this just another tracker that will let me down?' from the PCO Operator profile. Acknowledge this experience, then use it to pivot to the difference between consumer-grade OBD trackers and hardwired professional-grade solutions. Do not dismiss the concern — validate it and resolve it."
}
```

### do_not_use
```json
{
  "usage_role": "do_not_use",
  "usage_notes": "Duplicates the insurance reduction statistic already assigned as primary_claim from the BVRLA source. No additional value for this section."
}
```
