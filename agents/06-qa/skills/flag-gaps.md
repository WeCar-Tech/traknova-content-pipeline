# Skill: Flag Gaps

## Purpose
Identify every place in the article where something is missing, unsupported, incomplete, or requires a decision before the article can be published. Gaps are different from flow, tone, or alignment problems — they are absences rather than errors. A gap is a place where the article makes a claim without evidence, skips a logical step the reader needs, leaves a question unanswered that the article raised, or contains content that requires founder review or external verification before it can go live.

## When to apply this skill
Apply to the full draft as part of the QA agent's Step 3. Also cross-reference the run_log — any section flagged as skipped, partially synthesised, thin research, or requiring founder review during earlier pipeline stages must appear as a gap in this skill's output.

## What this skill produces
A structured list of gap findings, each with a location, impact description, and recommended action. If no gaps are found, return "flag-gaps: no gaps found."

---

## The checks

### Check 1 — Unsupported claims
Read every claim in the full draft that asserts a fact, statistic, outcome, or trend. For each claim, assess whether it is supported by evidence established in the article or traceable to a source in the context object's filtered_findings.

Flag if:
- A specific statistic is cited without a named source
- A claim about what "most operators" or "many fleets" do or experience is made without supporting data
- A cause-and-effect relationship is stated as fact without evidence — "tracking reduces insurance premiums" stated as a certainty rather than supported by cited data
- A claim appears that was not in the key_points for that section — this may indicate the writing agent introduced information not grounded in the research

For each flagged claim:
- Identify the claim exactly
- State whether the source exists in filtered_findings but was not cited, or whether no supporting source exists at all
- Recommend whether to add a citation, qualify the claim, find supporting evidence, or remove the claim

Severity guide:
- Claim exists in filtered_findings but was not cited in the draft — minor
- Claim is an approximation of a finding but overstates it — moderate
- Claim has no basis in filtered_findings and cannot be verified — major

---

### Check 2 — Logical gaps
Read the article's argument as it develops from section to section. Identify any place where the reader is asked to accept a conclusion that has not been sufficiently established, or where a logical step has been skipped.

Flag if:
- The article moves from identifying a problem to asserting a solution without explaining the mechanism that connects them
- A section's conclusion relies on information that was not introduced in that section or any previous section
- The article makes an implicit assumption about the reader's situation that may not be true for all readers in the target ICP
- A counter argument is raised in one section and resolved, but the resolution relies on a claim that has not been established elsewhere in the article
- The narrative thread calls for a specific logical progression that the draft does not follow

Severity guide:
- Minor logical step skipped that most readers would fill in themselves — minor
- A key part of the argument is assumed rather than established — moderate
- The article's central conclusion does not follow from its evidence — major

---

### Check 3 — Unanswered questions
Read the article from the perspective of the target ICP. Identify any question the article raises — explicitly or implicitly — that it does not answer.

Flag if:
- A section introduces a problem or challenge and the article never explains how it can be addressed
- A section references a concept, regulation, or situation the ICP may not be familiar with and does not explain it
- The introduction makes a promise — "this article will show you X" or "by the end of this you will understand Y" — that the article does not deliver on
- A statistic or claim is likely to prompt a "how?" or "why?" from the reader and the article does not address it
- The conclusion raises the possibility of a next step without giving the reader enough information to take it

Severity guide:
- Question is raised and partially answered — minor
- Question is raised and not answered — moderate
- A promise made in the introduction is not delivered — major

---

### Check 4 — Skipped and flagged sections
Cross-reference the run_log. For every section that was flagged as skipped, partially synthesised, or thin research during the research, analysis, or synthesis stages, confirm whether the article handles it appropriately.

Flag if:
- A section was marked as skipped due to insufficient research coverage and the draft contains a placeholder flag — this must appear in the QA report so the human reviewer knows it requires attention
- A section was partially synthesised and the resulting draft is noticeably thinner than other sections — the human reviewer must be aware of this limitation
- A section flagged as thin research in run_log appears in the draft with specific claims that are not grounded in the limited findings available — the writing agent may have filled gaps with unsupported content

For each instance:
- Identify the section
- State what the run_log records about it
- Assess whether the draft handles the limitation honestly or masks it
- Recommend specific action

Severity guide:
- Section is thin but the draft reflects that honestly — minor
- Section is thin and the draft overstates the evidence — major
- Section contains a placeholder flag requiring human input — major

---

### Check 5 — Founder review requirements
Read the full draft and identify every piece of content that falls under the topics and positions to avoid in brand-pov.md, or that was flagged for founder review during the writing stage.

Flag if:
- Any sentence makes a specific guarantee about insurance premium reductions — percentage figures, definitive outcomes, or language that implies certainty about a variable commercial outcome
- Any sentence names a competitor directly in a way that could create a reputational or legal issue
- Any sentence makes a specific regulatory claim — stating that a particular regulation requires a specific action, carries a specific penalty, or applies in a specific way — without a cited source and without founder verification
- Any sentence makes a claim about Traknova's product capabilities that goes beyond what is established in brand-pov.md
- Any content was flagged for founder review in run_log during the writing stage

For each instance:
- Quote the exact sentence or passage
- State the reason it requires founder review
- Recommend how to handle it pending the founder's decision — options are: qualify the claim, remove the claim, replace with a softer version, or publish as is with founder approval

Severity: every founder review requirement is major regardless of how minor the content appears.

---

### Check 6 — Search and LLM visibility gaps
Read the full draft and identify any structural or content gap that reduces the article's visibility to search engines or citability by LLMs.

Flag if:
- The article does not contain a single directly quotable sentence that states its central argument precisely enough to stand alone as a citable claim
- The primary keyword does not appear in the introduction
- The primary keyword does not appear naturally in at least two body sections
- Any section heading is vague, generic, or does not signal clearly what that section covers
- The conclusion does not restate the article's central argument in its most precise form
- The article does not answer the question implied by its headline directly enough for an LLM to extract a useful answer from the introduction alone
- The article relies entirely on secondary research with no original insight, position, or ICP-specific framing that would differentiate it from other content on this topic

Severity guide:
- One or two keyword placement gaps — minor
- Section headings are consistently vague — moderate
- Article contains no citable sentence and no original position — major

---

## Output format

For each gap found:

GAP — CHECK [number] — [check name]
Location: [section heading or quoted sentence]
Gap: [one sentence describing specifically what is missing]
Impact: [one sentence describing what this gap does to the reader experience or article argument]
Severity: [minor / moderate / major]
Recommended action: [specific instruction — add citation, rewrite, find evidence, flag for founder review, etc.]

If no gaps found for a check: GAP — CHECK [number] — [check name]: no gaps found.
