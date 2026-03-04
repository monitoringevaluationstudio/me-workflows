---
description: Review an evaluation Terms of Reference for methodological rigor, scope feasibility, ethical compliance, team composition, budget realism, and internal consistency
argument-hint: "[paste your TOR or describe the evaluation]"
---

# /tor-review -- Evaluation TOR Review

Review an evaluation Terms of Reference against established evaluation standards. Produces a scored review across 10 sections with issue classification (Critical/Important/Minor) and priority action list.

## Invocation

```
/me-workflows:tor-review

[paste your TOR here]
```

## Workflow

### Step 1: Accept Input

Accept the TOR in any of these formats:
- **Full document:** Complete TOR text
- **Document extract:** Key sections from a larger document
- **Narrative description:** User describes the evaluation and TOR contents
- **File reference:** User points to a document to review

If invoked with `$ARGUMENTS`, treat that as the TOR content to review.

If no TOR is provided, prompt the user to supply one. If the user describes a planned evaluation without a TOR, help them identify what the TOR should contain.

### Step 2: Classify Document Type

Identify the document type before reviewing (see skill methodology for classification table). State the document type at the top of the review and calibrate expectations accordingly.

For commissioning briefs or drafts, note which sections are present and which need development — don't simply fail every missing section.

For narrative descriptions, flag any sections where the description is silent as "not confirmed present" rather than "missing."

### Step 3: Conduct 10-Section Review

Review in this sequence, scoring each section PASS / PARTIAL / FAIL:

1. **Completeness** — All 10 standard sections present?
2. **Evaluation Questions** — Map to DAC criteria? Answerable? Specific? Not too many?
3. **Methodology** — Methods match questions? Feasible? Budget supports approach?
4. **Ethics** — IRB, consent, do-no-harm, data protection, vulnerable populations?
5. **Team & LOE** — Qualifications specific? National expertise? LOE realistic?
6. **Timeline** — Adequate time per phase? Review cycles defined?
7. **Budget** — Ceiling provided? Inclusions/exclusions clear? Matches ambition?
8. **Standards Alignment** — Aligned with OECD-DAC, UNEG, and any named donor's evaluation standards?
9. **Practical Readiness** — Data sources listed? Prior evaluations referenced? Language needs? Dissemination plan?
10. **Internal Consistency** — Cross-check: scope vs. budget, questions vs. methodology, timeline vs. deliverables, team vs. methodology, ethics vs. scope?

### Step 4: Classify Issues by Severity

For each finding, classify:
- **Critical (must fix):** Would make evaluation unethical, infeasible, or unable to answer its questions
- **Important (should fix):** Would significantly reduce quality or create implementation problems
- **Minor (nice to fix):** Best practice improvements that won't derail the evaluation

### Step 5: Calculate Overall Rating

Based on section scores:
- **Strong:** 0 FAIL, max 1 PARTIAL
- **Adequate:** 0 FAIL, 2+ PARTIAL
- **Needs Revision:** 1 FAIL, or 3+ PARTIAL
- **Major Issues:** 2+ FAIL

### Step 6: Generate Output

Produce the structured review with summary table, strengths, classified issues with specific fixes, and detailed findings.

When recommending changes, provide specific language the user can insert, not just abstract advice.

## Output Format

```
## TOR Review Summary

**Document:** [Title/reference]
**Document Type:** [Full TOR / Commissioning Brief / SOW / RFP / Draft]
**Evaluation Type:** [Performance / Impact / Process / Formative / Other]
**Overall Rating:** [Strong / Adequate / Needs Revision / Major Issues]

### Section Scores

| Section | Rating | Key Finding |
|---------|--------|-------------|
| Completeness | [PASS/PARTIAL/FAIL] | [one-line summary] |
| Evaluation Questions | [PASS/PARTIAL/FAIL] | [one-line summary] |
| Methodology | [PASS/PARTIAL/FAIL] | [one-line summary] |
| Ethics | [PASS/PARTIAL/FAIL] | [one-line summary] |
| Team & LOE | [PASS/PARTIAL/FAIL] | [one-line summary] |
| Timeline | [PASS/PARTIAL/FAIL] | [one-line summary] |
| Budget | [PASS/PARTIAL/FAIL] | [one-line summary] |
| Standards Alignment | [PASS/PARTIAL/FAIL] | [one-line summary] |
| Practical Readiness | [PASS/PARTIAL/FAIL] | [one-line summary] |
| Internal Consistency | [PASS/PARTIAL/FAIL] | [one-line summary] |

### Strengths
- [What the TOR does well]

### Critical Issues (Must Fix)
1. [Issue — why it matters — specific fix]

### Important Issues (Should Fix)
1. [Issue — why it matters — specific fix]

### Minor Improvements
1. [Improvement — rationale]

### Detailed Findings
[Section-by-section analysis with specific references to TOR text]
```

## Notes

- A TOR is a commissioning document, not a methodology. It should set parameters, not prescribe every detail. Evaluators need room to propose their approach.
- Calibrate expectations to the document type. A commissioning brief is intentionally incomplete.
- Consider context: a $30K evaluation of a small project has different expectations than a $500K multi-country impact evaluation.
- If the TOR is generally strong, say so. Not every TOR needs major revision.
- **Post-hoc review:** If the evaluation is already underway or completed, reframe Critical/Important findings as lessons for future TOR development — not required fixes.
- For program design review beyond the evaluation scope, use `/me-workflows:logframe-review`.
