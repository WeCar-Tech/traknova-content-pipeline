# Skill: Evaluate Source Credibility

## Purpose
Score each research finding for credibility before it is passed to the analysis agent. This skill does not filter findings out — that is the analysis agent's job. It adds a credibility score and classification to each finding so the analysis agent can make informed decisions about how much weight to give each source.

## When to apply this skill
Apply this skill to every finding in research_findings before the research agent passes the context object forward. Every finding must have a credibility assessment appended to it before leaving the research stage.

## What to add to each finding object
Append the following fields to each finding object:

- credibility_score: a number from 1 to 5 (see scoring guide below)
- source_classification: one of the classifications from the list below
- credibility_notes: one or two sentences explaining the score — be specific, not generic

---

## Source classifications

Assign one classification to each finding based on the source type:

| Classification | Description |
|---|---|
| government | Official UK government bodies, agencies, and regulators — DVSA, DVLA, TfL, HSE, GOV.UK |
| industry_body | Trade associations, professional bodies, and industry groups — BVRLA, FTA, RHA, ACFO, ABI |
| academic | Peer-reviewed research, university studies, and independent research institutions |
| news | Established news outlets with editorial standards — BBC, The Guardian, Fleet News, Motor Transport, Commercial Fleet |
| independent_research | Reports and studies from consultancies, think tanks, or research firms that are not selling a product |
| forum | Reddit posts, industry forums, operator communities — valuable for real operator sentiment, lower factual authority |
| vendor | Content produced by a company selling a product or service in this space — useful only if it contains third party data or named case studies |
| unknown | Source type cannot be determined |

---

## Credibility scoring guide

### Score 5 — High credibility
- Government or industry body source
- Data or claims are cited with a clear methodology or source reference
- Published or updated within the last 2 years
- Directly relevant to the UK market
- No commercial interest in the claims being made

### Score 4 — Good credibility
- Established news outlet or independent research report
- Claims are supported with named sources or data points
- Published within the last 3 years
- Primarily UK-focused or contains UK-specific data
- Minor commercial interest possible but not the primary purpose of the content

### Score 3 — Moderate credibility
- Forum post or community discussion with substantive content and meaningful engagement (10 or more comments, 10 or more upvotes)
- Vendor content that contains specific named case studies or third party statistics with a cited source
- News or research content older than 3 years but still likely to be current
- Content that is relevant but not UK-specific

### Score 2 — Low credibility
- Forum post with low engagement (fewer than 10 upvotes or fewer than 5 comments)
- Vendor content that contains data but does not cite the source
- Content published more than 3 years ago on a topic that changes frequently (insurance rates, regulations, technology)
- Content that is only partially relevant to the section topic

### Score 1 — Minimal credibility
- Anonymous content with no verifiable source
- Vendor marketing content with no data, no case studies, and no third party references
- Content that is tangentially related but requires significant inference to connect to the section topic
- Duplicate or near-duplicate of a finding already in the section

---

## Credibility notes rules
- Be specific — do not write "this is a reliable source". Write why: "Published by BVRLA in 2024, citing ABI insurance data — high authority for insurance cost claims"
- Flag any conflict of interest explicitly: "Published by a GPS tracking vendor — treat statistical claims with caution unless independently verified"
- Flag if the content is older than 3 years: "Published 2020 — regulation and insurance data may be outdated, verify before use"
- Flag if the content is not UK-specific: "US-based source — data may not reflect UK market conditions"

---

## Rules
- Every finding must be scored — do not skip findings even if the score is 1
- Do not remove findings based on score — low scoring findings may still be useful as context or counter-arguments
- Do not inflate scores to make the research look stronger than it is
- If you cannot determine the publication date, note this in credibility_notes and default to score 2
- If the source URL is inaccessible or returns an error, score it 1 and note "URL inaccessible — content unverified"

---

## Example output

```json
{
  "source_type": "industry_body",
  "source_url": "https://www.bvrla.co.uk/resource/fleet-insurance-report-2024.html",
  "source_title": "BVRLA Fleet Insurance Report 2024",
  "date_published": "2024-03-01",
  "raw_content": "Fleet operators with telematics installed reported an average 12% reduction in insurance premiums at renewal compared to non-telematics fleets.",
  "query_used": "fleet tracking insurance reduction UK independent report",
  "credibility_score": 5,
  "source_classification": "industry_body",
  "credibility_notes": "Published by BVRLA in 2024 with cited methodology. UK-specific data directly relevant to insurance reduction claims. No commercial interest in the finding."
}
```
