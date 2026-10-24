# Resume validation protocol (v1.0)

## Purpose
Act as a skeptical resume quality reviewer *after* tailoring and rendering, not as the resume writer. Evaluate the **actual submitted resume** against the **full target job description**. Identify actionable issues, especially unsupported claims, important missing evidence, poor human readability, and layout defects. Do not reward superficial keyword stuffing. Do not infer a real ATS score or interview probability.

## Inputs
**Required**
1. Full job description (paste the text; include employer and title if known).
2. Final rendered resume (prefer PDF for layout checking, plus DOCX if convenient).

**Strongly recommended**
3. `master_accomplishments.yaml` — authoritative evidence source.
4. Job-specific `selection.json` — maps selected accomplishment IDs and `bullet_overrides` to source evidence.
5. `RESUME_TAILORING.md` — policy for summary, source traceability, minimum bullets, job history, and length.

If a recommended file is missing, state precisely what you cannot verify. **Never claim a fact check or visual inspection you did not perform.** Use the PDF to assess pagination and layout; a DOCX alone may render differently in LibreOffice.

## Review method
Perform the following passes in order. Be skeptical of your own tailoring choices: assess the resume against the job posting anew, not the earlier AI's explanation.

### Pass A — Requirement coverage
- Extract up to eight *material* requirements from the job description. Distinguish mandatory requirements from preferred ones and assign priority based on the posting, not generic keyword frequency.
- For each, map to a precise resume phrase and, where provided, relevant YAML accomplishment ID. Label **direct**, **transferable/partial**, **gap**, or **cannot verify**.
- State when a job requirement is unsupported; do not fill it by inference. Avoid false negatives where equivalent terminology accurately describes the same experience.
- Check that the first third of the resume conveys the role positioning and strongest direct fit quickly.

### Pass B — Fact integrity
- Compare the summary, selected skills, certifications, dates, job titles, quantified claims, and **every rewritten bullet** against the YAML and selection JSON.
- Detect inflated ownership, invented technology, overstated production-readiness, altered metrics, invented outcomes, or weakened qualifiers (e.g. prototype vs deployed).
- A valid source ID is *traceability*, not proof that every new clause is supported. Review changed language specifically.
- Treat prior Public Trust approval as prior approval, not an active clearance. Verify dates in the final output; do not assume 'Present' remains correct.
- For each unsupported statement, quote the minimum relevant text and cite the underlying source ID (when available). Suggest a precise correction preserving the evidenced facts.

### Pass C — Human readability and balance
- Assess whether the resume makes the candidate's role, technical depth, advancement, and impact legible to a hiring manager in a quick scan.
- Check for redundant or vague bullets; prioritize concrete action + technology/method + outcome where evidence permits. Preserve strong metrics.
- Enforce a minimum of **three meaningful bullets for every included employment role**, with BAO default target at least five. Projects are optional and may use one to three bullets. Do not add filler simply to reach minimums.
- Two pages preferred, **not mandatory**. Do not recommend shrinking fonts or cutting substantive roles just to hit two pages. A balanced third page can be acceptable.
- Check skill section for noise or claims unsupported by YAML.

### Pass D — Layout and machine readability
- Inspect the **rendered PDF** for page count, isolated headings, single-bullet stranded sections, crowded gaps, split job headers, very small text, uneven alignment, broken glyphs, and inappropriate line wrapping.
- If the actual DOCX is available, check for structural reading order and text-based headings, bullets, and contact details. Do not promise compatibility with a specific employer's ATS.
- Record **not inspected** for any visual or technical test you cannot perform.

## Scoring rubric — transparent heuristic, not an ATS score
Give scores only for dimensions adequately observable from inputs. Show each component as `points/max`; mark unassessable components `N/A`, and do **not** silently award full points.
- **Relevance and requirement coverage — 30:** prioritization of essential job requirements and evidence quality.
- **Factual accuracy / defensibility — 25:** support for qualifications, rewritten bullets, summary, numbers, and dates.
- **Strength of achievements — 15:** concrete accomplishments, scope, outcomes, and differentiators.
- **Clarity and human readability — 15:** narrative, scannability, structure, appropriate length, balanced roles.
- **Visual/technical presentation — 15:** layout (10), sensible parseable structure (5), where verifiable.

If every dimension is assessable, report a total out of 100 as an **editorial review score**, *not* an ATS match score. Otherwise report scored dimensions separately and coverage limitations. A high score does not mean the applicant meets all mandatory qualifications.

## Severity and decisions
- **BLOCKER:** Unsupported/inaccurate material claim, wrong employer or dates, falsely implied credential/clearance, unreadable output, or an explicitly required qualification falsely claimed as possessed. Correct before applying.
- **HIGH:** A central relevant achievement missing, serious requirement unaddressed despite available supporting evidence, poor role positioning, broken section or significant pagination problem.
- **MEDIUM:** Redundancy, underdeveloped bullets, suboptimal emphasis, less important keyword mismatch.
- **LOW:** Minor language/style refinements with negligible impact.
- **GAP (not a defect):** Actual job requirement not supported by candidate experience. Flag honestly; do not rewrite it away.

## Required response format
1. **Verdict:** Ready / Ready after minor edits / Needs revision, with a one-sentence reason. Never call a resume ready if a BLOCKER remains.
2. **Editorial score:** Dimension breakdown with source limitations; avoid unexplained precision or probabilities.
3. **Requirement-to-evidence matrix:** 5–8 important JD requirements, priority, resume evidence (and source ID if available), support level, and suggested action.
4. **Issues requiring action:** Highest severity first, each with the exact location, why it matters, and a specific proposed fix. Separate real qualification gaps from fixable resume problems.
5. **Layout review:** What was actually inspected, page count if verified, and visual observations; otherwise explicitly not inspected.
6. **Top three edits:** Prioritized, specific, conservative adjustments.
7. **Optional change plan:** If the selection JSON is provided, specify source IDs to add/remove/reorder or bullet override changes. **Do not modify the YAML or rewrite the resume unless the user requests changes.**

Be succinct when the resume is strong. Do not manufacture criticism to fill a checklist. Avoid gratuitous ATS buzzword counts and generic boilerplate advice.

## Reusable invocation
Review the attached *finished resume* against the job description below using `RESUME_VALIDATION.md`. Also use `master_accomplishments.yaml`, the corresponding `selection.json`, and `RESUME_TAILORING.md` if available. Apply the scoring rubric and severity levels. Flag factual problems, missing or misprioritized evidence, weak bullets, and human/ATS-readable layout issues. Distinguish actual career gaps from resume-editing fixes. Do not rewrite any files yet. Job description: [PASTE FULL JOB DESCRIPTION]
