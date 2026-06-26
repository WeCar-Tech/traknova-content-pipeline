# Skill: Construct Search Queries

## Purpose
Generate targeted, high-signal search queries for a given article section. Queries must be specific enough to return results that are directly useful for that section — not generic results about the broader topic.

## Inputs you have access to
- Section heading
- Article goal
- ICP profile fields: who_they_are, what_they_care_about, core_pains_to_address
- Brand POV fields: core belief, what every article should reinforce

---

## Step 1 — Read the section heading and identify intent

Scan the section heading for the following trigger words and phrases. The first match determines the primary intent signal for your Serper queries. If multiple triggers match, use the first one in the list.

| Trigger words in heading | Primary intent signal | Secondary intent signal |
|---|---|---|
| why, reason, cause, leads to | pain point | data |
| problem, challenge, struggle, issue, risk, danger, threat | pain point | case study |
| how, steps, guide, ways to, approach | practical | case study |
| cost, costs, save, saving, expensive, price, ROI, worth | financial impact | data |
| law, legal, regulation, comply, compliance, fine, penalty, DVSA, TfL | regulatory | data |
| prove, evidence, proof, claim, dispute, incident | evidence | case study |
| what is, explained, overview, introduction, understanding | explainer | practical |
| choose, compare, difference, vs, best, right | comparison | practical |
| future, trend, changing, growing, increasing | trend | data |

If no trigger words match, default to: pain point as primary, data as secondary.

---

## Step 2 — Construct 3 Serper queries

### Query structure
Each query combines:
- The core topic of the section (extracted from the heading — strip filler words like "the", "a", "an", "your")
- An ICP-specific qualifier (a term this ICP would actually use or search for — draw from who_they_are and core_pains_to_address)
- An intent signal keyword (from the table above)
- A UK qualifier (see rules below)

### UK qualifier rules
Include a UK qualifier in every query unless the section topic explicitly concerns global data, international standards, or non-UK-specific technology. The following qualifiers are available — choose the one most specific to the ICP:
- "UK" — default for all ICPs
- "UK fleet" — for Fleet Services and Logistics ICPs
- "TfL" or "PCO" — for PCO Operator ICP where section is London-specific
- "DVSA" — for compliance and regulatory sections targeting Fleet Services or Logistics
- "UK dealership" — for Car Dealership ICP

### Query length
Aim for 4 to 8 words. Fewer than 4 words is too broad and will return generic results. More than 10 words risks over-constraining the query and returning no results.

### The 3 queries must cover 3 different angles
- Query 1: primary intent signal from Step 1
- Query 2: secondary intent signal from Step 1
- Query 3: a source-type angle — target a specific type of source that would be useful for this section, such as "report", "statistics", "forum", "review", "case study", or "insurance data"

### Rules
- Write in plain keyword style — no question marks, no quotation marks, no boolean operators
- Never use Traknova's brand name in a query
- Never use competitor brand names in a query
- Deprioritise vendor domains in results — if the top results are all vendor marketing pages, add "forum" or "independent" or "report" to the query to shift the result type
- Each query must be meaningfully different from the others — do not repeat the same keywords with minor variations

### Example — PCO Operator ICP
Section heading: Why PCO drivers pay more for insurance than standard car owners

Step 1 result: trigger word "why" → primary intent = pain point, secondary = data

Query 1 (pain point): PCO driver insurance costs UK challenges
Query 2 (data): private hire vehicle insurance statistics UK 2024
Query 3 (source-type): fleet tracking insurance reduction UK independent report

### Example — Logistics Fleet Manager ICP
Section heading: How poor driver behaviour increases fuel costs across a large fleet

Step 1 result: trigger word "how" → primary intent = practical, secondary = case study

Query 1 (practical): driver behaviour fuel cost reduction UK fleet
Query 2 (case study): fleet telematics fuel saving case study UK logistics
Query 3 (source-type): HGV driver behaviour monitoring statistics DVSA report

---

## Step 3 — Construct 2 Apify Reddit queries

### Subreddit selection
Select 2 subreddits from the following list based on the ICP profile. If an article targets multiple ICPs, select the 2 subreddits most relevant to the section topic.

| ICP | Primary subreddit | Secondary subreddit |
|---|---|---|
| PCO Operator | r/UKpersonalfinance | r/CarTalkUK |
| Taxi Company Owner | r/UKpersonalfinance | r/CommercialVehicles |
| Car Rental Firm Owner | r/CarTalkUK | r/AskUK |
| Car Dealership Owner or Manager | r/CarTalkUK | r/CommercialVehicles |
| Field Services Fleet Manager | r/CommercialVehicles | r/AskUK |
| Logistics Fleet Manager | r/CommercialVehicles | r/UKpersonalfinance |

Note: These subreddits are selected for UK relevance and activity level. They are broader communities where UK operators and vehicle owners discuss real problems. Use tight keyword queries to filter for section relevance.

### Reddit query structure
Each Reddit query must be a short keyword phrase of 2 to 5 words directly related to the section topic. Do not add intent signals — Reddit returns conversational content naturally and over-specified queries will return no results.

### Reddit result filters
- Include posts and comments
- Minimum 5 upvotes on posts
- Exclude posts older than 3 years
- Prioritise threads with more than 10 comments — these indicate genuine discussion

### Example — PCO Operator ICP
Section heading: Why PCO drivers pay more for insurance

Query 1 (r/UKpersonalfinance): private hire insurance costs
Query 2 (r/CarTalkUK): PCO vehicle insurance

---

## Step 4 — Define a useful result

A result is useful if it meets all of the following criteria:
- It contains a direct reference to the section topic — not just the broader subject area
- It is published by a non-vendor source: a news outlet, industry body, government body, forum post, independent review, or research report. Vendor content is only useful if it contains specific data, a named case study, or a quoted statistic from a third party source
- It was published or last updated within the last 3 years
- It is in English and primarily concerns the UK market or contains UK-specific data

A result is not useful if:
- It is a product listing, pricing page, or vendor feature overview with no supporting data
- It is older than 3 years with no indication the information is still current
- It is behind a paywall with no accessible excerpt
- It is a duplicate of a result already collected for this section

---

## Step 5 — Retry logic

If a query returns fewer than 3 useful results after the first run, apply the following in order:

1. Remove the most specific qualifier (usually the ICP-specific term) and run the query again
2. If still fewer than 3 useful results, replace the intent signal keyword with the secondary intent signal from Step 1 and run again
3. If still fewer than 3 useful results after two retries, log the section as "thin research — [section heading] — [query used]" in run_log and move on

Do not fabricate results. Do not lower the definition of a useful result to meet a quota. Thin research is better than bad research.
