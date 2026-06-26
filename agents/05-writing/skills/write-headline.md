# Skill: Write Headline

## Purpose
Produce the headline the article will be published under. The headline is not the article title from the brief — it is the first thing the target reader sees and the primary reason they decide to read or scroll past. It also carries significant weight for search engine ranking and LLM citability. A strong headline makes a specific promise to a specific reader, signals topical relevance to search engines, and is structured clearly enough that an LLM can identify what the article is about from the headline alone.

## When to apply this skill
Apply once before writing any section, as part of the writing agent's Step 2.

## What this skill produces
Three headline options with a recommended choice and rationale. The writing agent selects the recommended option unless instructed otherwise in the brief.

---

## How to write the headline

### Step 1 — Extract the raw ingredients
From the context object, extract and hold in working memory:
- The central argument from narrative_thread
- The opening intent from narrative_thread
- The target ICP's core_pains_to_address — specifically the pain most central to this article
- The target ICP's conversion_goal
- The article_goal
- Any SEO keywords or target phrases listed in the brief's additional instructions

### Step 2 — Identify the primary keyword
The primary keyword is the term or phrase the target ICP is most likely to search when looking for content that answers the question this article addresses. It must be:
- A phrase the ICP would actually use — not industry jargon, not Traknova terminology
- Specific enough to signal clear search intent — "fleet tracking" is too broad, "fleet tracking insurance UK" is specific
- Naturally incorporable into the headline without forcing it

If the brief specifies a target keyword, use it. If not, derive it from the ICP profile's language_and_tone.use field and the section headings in the article.

The primary keyword should appear in the headline, ideally in the first half. Do not force it in a way that makes the headline read awkwardly — readability takes priority over keyword placement if there is a conflict.

### Step 3 — Identify search intent
Every headline must match the search intent behind the primary keyword. Identify which intent applies:

- informational — the reader wants to understand something. They are in research mode. Headlines should signal explanation, insight, or revelation.
- navigational — the reader is looking for a specific resource or tool. Less common for Traknova content.
- commercial investigation — the reader is evaluating options before making a decision. Headlines should signal comparison, evidence, or proof.
- transactional — the reader is ready to act. Headlines should signal a clear next step or outcome.

Most Traknova articles will target informational or commercial investigation intent. The headline must signal the correct intent — a commercial investigation reader who clicks an informational headline will bounce immediately.

### Step 4 — Identify the headline type
Choose the headline type that best fits the article's central argument, opening intent, and search intent:

- problem headline — names the specific pain the ICP is experiencing. Works best for informational intent when the article opens by establishing the problem. Example: "Why PCO Drivers Are Overpaying for Insurance — And What the Data Shows"
- outcome headline — leads with the result the reader wants. Works best for commercial investigation intent. Example: "How Fleet Operators Are Using Tracking Data to Cut Insurance Costs at Renewal"
- challenge headline — reframes a common assumption or reveals something the reader does not know yet. Works best for informational intent when the article introduces a turning point. Example: "Your Insurer Is Not Guessing Your Premium — They Are Reading Signals You Are Sending Without Knowing"
- direct headline — states the article's central argument plainly. Works best for practical how-to articles targeting informational or transactional intent. Example: "How to Use Telematics Data to Negotiate a Lower Fleet Insurance Premium"
- stakes headline — establishes what is at risk if the reader does not act. Works best for commercial investigation intent when the article's argument is about urgency or consequence. Example: "The Cost of Running a Fleet Without Real-Time Visibility Is No Longer Just Operational"

### Step 5 — Write three headline options
Write one headline for each of the following:
- The headline type identified in Step 4 — this is the primary option
- The headline type that is the second best fit for this article
- A direct headline regardless of what was selected in Step 4 — this serves as a plain fallback

Each headline must:
- Contain the primary keyword identified in Step 2, ideally in the first half
- Be specific to the target ICP — a fleet manager and a PCO driver should not be interchangeable in the headline
- Contain a concrete element — a number, a specific outcome, a named situation, or a direct reference to the ICP's world
- Be between 8 and 16 words — long enough to be specific, short enough to read at a glance
- Be written in UK English
- Contain no em dashes
- Contain no corporate jargon
- Not start with "How to" unless the article is genuinely a practical step-by-step guide
- Be clear enough that an LLM can identify the article's topic and position from the headline alone

### Step 6 — Select and justify the recommended headline
Select the strongest of the three options and write two to three sentences explaining why it is the strongest choice for this specific article and this specific ICP. Reference the central argument, the opening intent, the primary keyword placement, and the search intent match in the justification.

---

## Rules
- Do not write clickbait — the headline must accurately represent what the article delivers
- Do not write a headline that overpromises — if the article does not guarantee a specific outcome, the headline must not imply it does
- Do not repeat the brief's working title as a headline option unless it genuinely meets all the criteria above
- Do not use the words "ultimate", "complete", "comprehensive", "definitive", or "everything you need to know"
- Do not use question headlines — they are weak and rarely outperform statement headlines
- SEO keywords from the brief must be incorporated naturally — do not force them in ways that make the headline read awkwardly
- The headline must match search intent — a mismatch between headline and intent will increase bounce rate and signal poor content quality to search engines

---

## Example output

Article: PCO insurance and tracking data
ICP: PCO Operator
Primary keyword: PCO insurance costs UK
Search intent: informational

Option 1 (problem headline — recommended):
"PCO Drivers Are Paying Over the Odds for Insurance. The Data Already Exists to Change That."
Rationale: Validates the reader's existing frustration immediately, matching the opening intent of making the reader feel understood. The second sentence introduces possibility without overpromising. Primary keyword concept is present naturally. Matches informational intent — the reader wants to understand why and what they can do. Clear enough for an LLM to identify the article's topic and position without reading further.

Option 2 (outcome headline):
"How UK Private Hire Operators Are Using Tracking Data to Lower Their Insurance Premiums"

Option 3 (direct headline):
"Fleet Tracking and Insurance Costs: What PCO Drivers Need to Know Before Their Next Renewal"
