# Skill: Check Tone

## Purpose
Assess whether the article's tone, voice, and language are consistent throughout and aligned with Traknova's brand POV and the target ICP's language preferences. Tone problems are often invisible to the writer but immediately felt by the reader — a single corporate phrase, an AI pattern, or a sentence that talks down to the reader can break the trust the article has been building.

## When to apply this skill
Apply to the full draft as part of the QA agent's Step 3. Read the entire article before identifying tone issues — a tone problem in one section is sometimes caused by a setup issue in an earlier section.

## What this skill produces
A structured list of tone findings, each with a location, severity, and recommended fix. If no tone issues are found, return "check-tone: no issues found."

---

## The checks

### Check 1 — UK English compliance
Read the full draft and flag any instance of non-UK English spelling, idiom, or phrasing.

Flag if:
- American spellings are used: "analyze" instead of "analyse", "color" instead of "colour", "license" as a noun instead of "licence", "optimize" instead of "optimise", "program" instead of "programme" where the UK form applies
- American idioms or expressions are used that a UK reader would notice as foreign
- Dates are formatted in US style: "June 23, 2026" instead of "23 June 2026"
- Currency is referenced without the pound sterling symbol or in US dollars where UK context applies

Severity guide:
- One or two instances — minor
- Multiple instances throughout — moderate
- Systematic use of US English — major

---

### Check 2 — Em dash compliance
Read the full draft and flag every instance of an em dash.

An em dash looks like this: —
It is never acceptable in any Traknova article under any circumstances.

Flag every single instance regardless of how it is used. There are no exceptions.

Severity: every instance is major.

Recommended fix for every instance: remove the em dash and restructure the sentence. Options:
- Replace with a full stop and start a new sentence
- Replace with a comma if the em dash was used as a parenthetical
- Replace with a colon if the em dash was introducing a list or elaboration
- Rewrite the sentence entirely if restructuring produces an awkward result

---

### Check 3 — Corporate jargon
Read the full draft and flag any instance of corporate jargon or marketing language that would sound out of place in a peer-level conversation between fleet operators.

Flag any instance of:
- "leverage" used as a verb
- "synergy" or "synergies"
- "ecosystem" used to describe Traknova's platform or market
- "unlock value" or "unlock potential"
- "cutting-edge", "game-changing", "industry-leading", "best-in-class"
- "seamless" used to describe any process or integration
- "robust" used to describe any system or solution
- "innovative" or "innovation" used as a label rather than demonstrated through substance
- "streamlined" without a specific description of what was streamlined and how
- "solution" used as a generic noun — "our solution", "the solution" — without specificity
- "space" used to mean industry or market — "the fleet management space"
- "empower" or "empowering"
- "holistic"
- "at the end of the day"
- "it goes without saying"
- "in today's world" or "in today's fast-paced environment"
- "now more than ever"
- "digital transformation"

Severity guide:
- One or two instances — minor
- More than three instances — moderate
- Pervasive throughout the article — major

---

### Check 4 — The three-sentence AI pattern
Read the full draft looking for the three-sentence AI pattern: broad statement, slightly more specific statement, conclusion that restates the first sentence.

Examples to flag:
- "Fleet security is important for any operator. Managing a fleet comes with significant risks. That is why having the right security measures in place matters."
- "Insurance costs are a major concern for PCO drivers. Many operators find premiums difficult to manage. Understanding what drives these costs is the first step."
- "Tracking technology has evolved significantly. Modern systems offer far more than basic location data. This gives operators more options than ever before."

Flag every instance. This pattern is the clearest signal of AI-generated content and must be eliminated entirely.

Severity: every instance is major.

Recommended fix: collapse the three sentences into one precise, specific sentence that says what the three were circling around.

---

### Check 5 — Peer-level tone
Read the full draft and assess whether it consistently maintains a peer-level tone — operator to operator, not brand to customer.

Flag if:
- Any sentence talks down to the reader — explains something the ICP already knows, uses over-simplified language, or treats the reader as uninformed
- Any sentence positions Traknova as an authority lecturing the reader rather than as a knowledgeable peer
- Any section shifts from operator-level language to marketing language without justification
- The article refers to the reader in a way that creates distance — "fleet operators" when "you" would be more direct, or "businesses like yours" which sounds like sales copy

Severity guide:
- One or two instances of patronising or distancing language — minor
- A full section that shifts to brand-voice rather than peer-voice — moderate
- The article consistently reads as brand-to-customer rather than peer-to-peer — major

---

### Check 6 — Tone consistency
Read the full draft and assess whether the tone established in the introduction is maintained throughout.

Flag if:
- The introduction establishes a direct, peer-level tone but later sections become more formal or corporate
- The introduction is cautious and measured but later sections become promotional
- Any section has a noticeably different voice from the rest of the article — more casual, more formal, more salesy, or more academic
- The conclusion shifts to a sales tone that is inconsistent with the peer-level voice established earlier

Severity guide:
- Minor tonal variation in one section — minor
- Significant tonal shift in one section — moderate
- Inconsistent tone throughout the article — major

---

### Check 7 — Filler phrases and weak language
Read the full draft and flag any instance of filler phrases or weak, hedging language that reduces the precision and authority of the article.

Flag any instance of:
- "very", "quite", "rather", "somewhat", "fairly" used as intensifiers
- "a number of", "a variety of", "various" — replace with a specific number or list
- "many operators", "most fleets", "some businesses" — replace with a specific reference or data point
- "may", "might", "could potentially", "in some cases", "it is possible that" — replace with a direct statement where the evidence supports it
- "as mentioned earlier", "as we discussed" — remove entirely
- "needless to say", "of course", "obviously" — remove entirely

Severity guide:
- Two or three instances — minor
- More than five instances — moderate
- Pervasive hedging language throughout — major

---

## Output format

For each issue found:

TONE — CHECK [number] — [check name]
Location: [section heading or quoted sentence]
Issue: [one sentence describing the specific problem]
Severity: [minor / moderate / major]
Recommended fix: [specific instruction — what needs to change and how]

If no issues found for a check: TONE — CHECK [number] — [check name]: no issues found.
