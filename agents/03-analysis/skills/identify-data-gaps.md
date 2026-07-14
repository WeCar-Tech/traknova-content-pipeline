# Skill: Identify Data Gaps

## Purpose
After all findings in a section have been scored for ICP relevance and checked for POV conflict, assess whether the filtered findings for that section provide sufficient coverage to write from. A section with thin, weak, or one-dimensional findings will produce a thin, weak, or one-dimensional draft. This skill catches that before it reaches the writing agent.

## When to apply this skill
Apply once per section after all findings in that section have received their icp_relevance_score and pov_conflict_status assessments. This is the third assessment in the analysis agent's Step 2 and operates at section level, not finding level.

## What to add to the section object
Append the following fields to each section object:

- coverage_status: one of "sufficient", "partial", or "insufficient" (see definitions below)
- coverage_notes: two to four sentences describing the state of coverage for this section — what is well covered, what is missing, and what type of source or angle would fill the gap
- gap_description: if coverage_status is "partial" or "insufficient", a specific one sentence description of what is missing. If coverage_status is "sufficient", leave as null.

---

## Coverage status definitions

### sufficient
The section has at least 3 passed findings (filter_status "pass" or "pass_with_caution") that together cover the section topic from at least 2 different angles. At least one finding has a credibility_score of 4 or 5 and an icp_relevance_score of 4 or 5. The writing agent has enough material to write a substantive, evidence-backed section.

### partial
The section has 1 or 2 passed findings, or has 3 or more passed findings but they all come from the same angle or source type, or none of the passed findings has both a credibility_score of 3 or above and an icp_relevance_score of 3 or above. The writing agent can produce a draft but it will be limited — the human reviewer should be aware.

### insufficient
The section has zero passed findings, or all findings were filtered out due to POV conflict, or the only passed findings have both a credibility_score of 2 or below and an icp_relevance_score of 2 or below. The writing agent should not attempt to write this section from the available findings alone.

---

## How to assess coverage

### Step 1 — Count passed findings
Count the number of findings in the section with filter_status "pass" or "pass_with_caution".

### Step 2 — Check score quality
Identify whether any passed finding has:
- credibility_score of 4 or 5 AND icp_relevance_score of 4 or 5 — this is a strong finding
- credibility_score of 3 or above AND icp_relevance_score of 3 or above — this is an adequate finding
- Both scores below 3 — this is a weak finding

### Step 3 — Check angle diversity
Review the source_classification of all passed findings. If all passed findings share the same source_classification — for example all are "forum" or all are "vendor" — the coverage is one-dimensional regardless of how many findings there are. Note this in coverage_notes.

### Step 4 — Identify what is missing
If coverage_status is "partial" or "insufficient", identify specifically what type of material is missing. Use the following categories to describe the gap:

- factual data — the section lacks statistics, figures, or verifiable facts
- operator sentiment — the section lacks real-world perspective from fleet operators or drivers
- regulatory context — the section lacks information about relevant laws, rules, or compliance requirements
- case study or example — the section lacks a concrete real-world example or outcome
- expert or authoritative source — the section lacks input from an industry body, regulator, or credible publication
- UK-specific context — the section has findings but none are specific to the UK market

---

## Rules
- Apply this skill after filtered_findings has been populated for the section — do not assess based on raw research_findings
- Do not adjust coverage_status based on how important the section is — a short introductory section and a core argument section are assessed by the same criteria
- Do not mark a section as sufficient simply because it has many findings — quantity does not equal coverage quality
- A section with 1 strong finding (credibility 5, ICP relevance 5) and nothing else is "partial" not "sufficient" — one source is never sufficient regardless of quality
-- If coverage_status is "partial" or "insufficient", this is captured directly via the section's own coverage_status and gap_description fields. Do not attempt to write to a shared run_log — this skill operates on a single section in isolation and has no visibility into other sections or a brief-wide log.
- Do not trigger a research retry — gap flags are for the human reviewer to act on

---

## Example outputs

### Sufficient
```json
{
  "coverage_status": "sufficient",
  "coverage_notes": "Section has 4 passed findings covering insurance cost data from BVRLA, operator sentiment from Reddit, a case study from a UK fleet news outlet, and regulatory context from GOV.UK. Two findings score 5 on both credibility and ICP relevance. Coverage is strong across multiple angles and source types.",
  "gap_description": null
}
```

### Partial
```json
{
  "coverage_status": "partial",
  "coverage_notes": "Section has 3 passed findings but all three are from forum sources with credibility scores of 3 or below. Operator sentiment is well covered but there is no factual data or authoritative source to anchor the claims. Writing agent can draft this section but it will lack evidential weight.",
  "gap_description": "Missing factual data — no statistics or authoritative source covering insurance cost differentials for PCO drivers specifically."
}
```

### Insufficient
```json
{
  "coverage_status": "insufficient",
  "coverage_notes": "All findings for this section were filtered out. Two findings conflicted with Traknova's POV on insurance guarantees and the remaining finding was a vendor marketing page with no supporting data. No material is available for the writing agent to work from.",
  "gap_description": "Missing all coverage — no passed findings remain after POV conflict filtering. Requires fresh research targeting independent UK sources on fleet compliance costs."
}
```
