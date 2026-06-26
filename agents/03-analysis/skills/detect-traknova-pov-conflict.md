# Skill: Detect Traknova POV Conflict

## Purpose
Identify whether a research finding conflicts with, undermines, or contradicts Traknova's stated brand position. A finding that conflicts with Traknova's POV can damage the credibility of the article, create mixed messaging, or put Traknova in a difficult position if published. This skill flags those findings before they reach the writing agent.

## When to apply this skill
Apply to every finding in research_findings as part of the analysis agent's Step 2. This is the second of three assessments every finding must receive.

## What to add to each finding object
Append the following fields:

- pov_conflict_status: one of "clear", "caution", or "conflict" (see definitions below)
- pov_conflict_notes: one or two sentences explaining the status — reference specific brand POV fields to justify it. If status is "clear", this field can be null.

---

## Status definitions

### clear
The finding does not conflict with any aspect of Traknova's brand POV. It either supports Traknova's position, provides neutral context, or addresses a topic Traknova has no stated position on.

### caution
The finding contains a claim, statistic, or perspective that is partially in tension with Traknova's POV but is not a direct contradiction. Examples:
- A finding that suggests fleet tracking has limited impact on insurance premiums when Traknova's POV emphasises the value of data for insurance purposes
- A finding from a competitor that contains useful data but also promotes a competing position
- A finding that makes a regulatory claim Traknova has not verified
- A finding that overstates the difficulty or cost of fleet technology in a way that could create unnecessary doubt

### conflict
The finding directly contradicts a stated Traknova position or falls into a category listed under topics and positions to avoid in brand-pov.md. Examples:
- A finding that makes guarantees about insurance premium reductions — brand-pov.md flags this as requiring founder review
- A finding that names a competitor positively in a way that undermines Traknova's positioning
- A finding that argues disconnected tools are sufficient — directly contradicts Traknova's core belief in connected systems
- A finding that suggests SME fleets do not need fleet intelligence technology

---

## How to assess each finding

### Step 1 — Load Traknova's POV
From brand-pov.md, extract and hold in working memory:
- Core belief
- What every article should reinforce
- What Traknova stands against
- Traknova's differentiators to reference in content
- Topics and positions to avoid

### Step 2 — Read the finding's raw_content and ask the following questions

1. Does this finding make a claim that directly contradicts any point in "what every article should reinforce"?
2. Does this finding argue for something Traknova stands against — disconnected tools, enterprise-only solutions, hardware-heavy approaches where digital alternatives exist?
3. Does this finding fall into any category listed under topics and positions to avoid — specific regulatory claims, competitor naming, insurance premium guarantees?
4. Does this finding undermine any of Traknova's differentiators — all-in-one platform, digital tracking layer, SME focus, automation-first approach?
5. Does this finding create a contradiction that would confuse the reader if it appeared alongside Traknova-aligned content?

If any answer is yes to questions 1, 3, or 4 — status is "conflict".
If any answer is yes to questions 2 or 5 — status is "caution".
If all answers are no — status is "clear".

---

## Rules
- Do not flag a finding as conflict simply because it presents a challenge or problem — Traknova's content can and should acknowledge real operator pain points
- Do not flag competitor mentions as automatic conflicts — a finding that references a competitor is only a conflict if it positively promotes that competitor or positions them as superior
- Do not flag findings that contain nuance or caveats as conflicts — real-world complexity is not a brand conflict
- A finding with pov_conflict_status "conflict" must not appear in filtered_findings under any circumstances
- A finding with pov_conflict_status "caution" may appear in filtered_findings with filter_status "pass_with_caution" and a clear caution_note explaining the tension and how to handle it in writing

---

## Example outputs

### Clear
```json
{
  "pov_conflict_status": "clear",
  "pov_conflict_notes": null
}
```

### Caution
```json
{
  "pov_conflict_status": "caution",
  "pov_conflict_notes": "Finding cites a study suggesting telematics reduces insurance premiums by up to 8% — useful data but lower than some market claims. Use carefully and avoid presenting as a guarantee. Aligns with Traknova's general position but should not be overstated."
}
```

### Conflict
```json
{
  "pov_conflict_status": "conflict",
  "pov_conflict_notes": "Finding makes a specific guarantee that GPS tracking reduces insurance premiums by 15% with no cited source. Brand-pov.md explicitly flags insurance premium guarantees as requiring founder review before publishing. Do not pass forward."
}
```
