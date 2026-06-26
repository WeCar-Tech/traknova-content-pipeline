# Skill: Extract Key Points

## Purpose
Extract the 2 to 4 most important points a section should make, based on the filtered findings and their assigned usage roles. These key points are the direct input the writing agent uses to draft each section. They must be specific, actionable, and framed for the target ICP — not generic summaries of what the research found.

## When to apply this skill
Apply to each section after evaluate-source-value.md has been run on all findings in that section. This is the second of two skills applied at section level before build-narrative-thread is run.

## What this skill produces
A key_points array for the section. Each entry in the array is a structured point object containing:

- point: the specific claim, argument, or insight the writing agent should make
- how_to_use: the role this point plays in the section
- source_reference: the source_url this point is drawn from, or null if synthesised across multiple findings
- icp_angle: how this point connects to what the target ICP cares about
- traknova_angle: how this point connects to or supports Traknova's POV

---

## How to extract key points

### Step 1 — Review usage roles
Look at all findings in filtered_findings for this section and their assigned usage_roles. Group them as follows:
- Primary claim findings — these anchor the section and must produce at least one key point
- Supporting evidence findings — these produce key points that reinforce the primary claim
- Real world example findings — these produce key points that illustrate the argument concretely
- Counter and resolve findings — these produce key points that pre-empt ICP objections
- Background context findings — these rarely produce standalone key points but may inform the framing of other points
- Do not use findings — ignore these entirely

### Step 2 — Draft candidate key points
For each finding with a usage role other than do_not_use or background_context, draft one candidate key point. A key point is not a summary of the finding — it is the argument or insight the finding supports. Ask: what should the writing agent say in this section, and how does this finding justify saying it?

### Step 3 — Select the strongest 2 to 4 points
From the candidate key points, select the 2 to 4 that together give the writing agent the best material to write a complete, coherent, ICP-relevant section. Apply the following selection criteria:

- The selected points must collectively cover the section topic — a reader who encounters only these points should come away with a complete understanding of what the section is arguing
- At least one point must be anchored in a finding with credibility_score 4 or 5
- At least one point must have a clear and specific icp_angle — something the target reader would immediately recognise as relevant to their situation
- If a counter_and_resolve finding exists, include it as a key point unless a stronger set of 4 points already addresses the same objection
- Do not select points that overlap significantly — each point should add something the others do not

### Step 4 — Assign how_to_use
For each selected key point, assign one of the following values to how_to_use:

- lead argument — this is the central claim the section is built around. Use it to open the section or establish the main point early. One per section maximum.
- supporting evidence — this reinforces the lead argument with additional data, context, or perspective.
- example — this illustrates the argument with a concrete real-world situation the ICP would recognise.
- counter and resolve — this acknowledges a reader objection and resolves it within the section.
- transition — this point closes the section and sets up the next one. Use sparingly and only when the section needs to create a clear bridge to what follows.

### Step 5 — Write icp_angle and traknova_angle for each point
These are not generic labels — they are specific instructions to the writing agent explaining how to frame this point for maximum relevance and alignment.

icp_angle must:
- Reference a specific field from the ICP profile — name the pain, belief, or objection it connects to
- Tell the writing agent what the reader is likely thinking or feeling in relation to this point
- Suggest how to frame the point so it speaks directly to this reader's situation

traknova_angle must:
- Reference a specific element of Traknova's brand POV — name the differentiator, belief, or position it supports
- Tell the writing agent how to connect this point to Traknova's position without making it sound like a sales pitch
- Flag if the point needs careful handling to stay within topics and positions to avoid

---

## Rules
- Do not produce more than 4 key points per section regardless of how many findings are available
- Do not produce fewer than 2 key points unless the section has coverage_status "partial" and only one strong finding exists — in that case produce 1 key point and note the limitation in run_log
- Do not copy finding content directly into the point field — the point is an argument, not a quote or paraphrase of a source
- Do not assign lead argument to more than one point per section
- Every point must be traceable to at least one finding in filtered_findings — do not invent points
- icp_angle and traknova_angle must be written as instructions to the writing agent, not as descriptions of the finding

---

## Example output

```json
{
  "key_points": [
    {
      "point": "PCO drivers pay disproportionately high insurance premiums relative to their actual risk profile, and the data exists to change this at renewal if it is captured and presented correctly.",
      "how_to_use": "lead argument",
      "source_reference": "https://www.bvrla.co.uk/resource/fleet-insurance-report-2024.html",
      "icp_angle": "Connects directly to 'high insurance premiums they feel powerless to reduce' from PCO Operator core_pains_to_address. The reader already feels this pain — open the section by validating it before introducing the data angle. Frame it as a solvable problem, not a permanent condition.",
      "traknova_angle": "Supports the brand POV that the future is data and that data already in the vehicle can change the operator's commercial position. Connect tracking data to insurance outcomes without making a specific premium reduction guarantee — stay within brand guidelines."
    },
    {
      "point": "Operators who have installed telematics and presented the data to their insurer at renewal have seen measurable reductions — this is not theoretical, it is already happening in the UK market.",
      "how_to_use": "supporting evidence",
      "source_reference": "https://www.bvrla.co.uk/resource/fleet-insurance-report-2024.html",
      "icp_angle": "Pre-empts the objection 'Will this actually reduce my insurance or is that a sales claim?' Use the BVRLA data to make this concrete. The reader is sceptical — lead with the source credibility before the statistic.",
      "traknova_angle": "Reinforces Traknova's differentiator around operational intelligence and data-driven fleet management. Position this as evidence that the connected system approach delivers real commercial outcomes, not just operational convenience."
    },
    {
      "point": "A PCO driver who had a cheap OBD tracker removed by a thief illustrates exactly why the type of tracking hardware matters as much as having tracking at all.",
      "how_to_use": "counter and resolve",
      "source_reference": "https://www.reddit.com/r/TaxiUK/comments/example",
      "icp_angle": "Directly addresses the objection 'Is this just another tracker that will let me down?' from PCO Operator objections_to_pre-empt. Validate the experience before resolving it — this reader has likely heard of or experienced cheap trackers failing. Do not dismiss the concern.",
      "traknova_angle": "Use this to draw a clear distinction between consumer-grade solutions and professional-grade hardwired tracking without naming competitors. Connects to Traknova's position on innovation and connected systems built for commercial operators."
    }
  ]
}
```
