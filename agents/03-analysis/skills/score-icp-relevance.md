# Skill: Score ICP Relevance

## Purpose
Score each research finding against the target ICP profile to determine how directly useful it is for the specific reader this article is written for. A finding can be factually accurate and credible but still score low here if it does not speak to what this ICP cares about.

## When to apply this skill
Apply to every finding in research_findings as part of the analysis agent's Step 2. This is the first of three assessments every finding must receive.

## What to add to each finding object
Append the following fields:

- icp_relevance_score: a number from 1 to 5 (see scoring guide below)
- icp_relevance_notes: one or two sentences explaining the score — reference specific ICP profile fields to justify it

---

## How to score

### Step 1 — Identify what this ICP cares about
From the ICP profile file, extract and hold in working memory:
- what_they_care_about
- core_pains_to_address
- beliefs_to_align_with
- objections_to_pre-empt

### Step 2 — Match the finding to ICP concerns
Read the finding's raw_content and ask the following questions:

1. Does this finding directly address something in what_they_care_about or core_pains_to_address?
2. Does this finding support or reinforce something in beliefs_to_align_with?
3. Does this finding provide evidence or context that would help pre-empt an objection in objections_to_pre-empt?
4. Is the finding set in a context this ICP would recognise — UK market, their industry, their fleet size, their role?
5. Would this finding make the target reader feel understood, informed, or more confident in a decision?

---

## ICP relevance scoring guide

### Score 5 — Directly relevant
The finding addresses a named pain, belief, or objection from the ICP profile. It is set in a context the ICP would immediately recognise. A writer could use this finding to make the reader feel directly spoken to.

### Score 4 — Clearly relevant
The finding is clearly about a topic the ICP cares about but does not map precisely to a named pain or belief. It provides useful supporting context that the ICP would find credible and interesting.

### Score 3 — Partially relevant
The finding touches on the ICP's world but from a different angle — for example, a finding about large enterprise fleets when the ICP is an SME operator, or a finding about a related industry rather than the ICP's specific sector. Useful as background but not directly speakable to this reader.

### Score 2 — Marginally relevant
The finding is about the broader topic area but does not connect clearly to this ICP's specific concerns. Would require significant reframing to be useful for this reader. Only use if no better alternatives exist.

### Score 1 — Not relevant to this ICP
The finding is about the topic but from a perspective entirely disconnected from this ICP — wrong industry, wrong fleet size, wrong geography, or wrong role. Would not resonate with this reader.

---

## Multi-ICP articles
If the article targets more than one ICP, score the finding against each ICP separately and record the highest score as the primary icp_relevance_score. Note in icp_relevance_notes which ICP the score applies to and how the other ICPs scored.

---

## Rules
- Always reference specific ICP profile fields in icp_relevance_notes — do not write generic notes like "relevant to fleet operators"
- Do not inflate scores because a finding is credible — credibility and ICP relevance are separate assessments
- Do not deflate scores because a finding is from Reddit — operator sentiment from a forum can score 5 if it directly expresses a named ICP pain
- A finding that perfectly addresses an objection in objections_to_pre-empt should score at least 4 even if it does not address a core pain

---

## Example output

```json
{
  "icp_relevance_score": 5,
  "icp_relevance_notes": "Finding directly addresses 'high insurance premiums they feel powerless to reduce' from the PCO Operator core_pains_to_address. UK-specific data from a private hire context the reader would immediately recognise. Supports the belief that proper security pays for itself over time."
}
```
