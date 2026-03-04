---
description: Review a survey instrument, questionnaire, KII guide, or FGD guide for design quality, question clarity, ethical compliance, sampling adequacy, and practical feasibility
argument-hint: "[paste your survey instrument or questionnaire]"
---

# /survey-review -- Survey Instrument Review

Review a data collection instrument against established survey design standards and M&E good practice. Produces a scored review across 6 dimensions with prioritized recommendations.

## Invocation

```
/me-workflows:survey-review

[paste your survey instrument here]
```

## Workflow

### Step 1: Accept Input

Accept the instrument in any of these formats:
- **Full instrument:** Complete questionnaire, KII guide, or FGD guide pasted as text
- **Partial instrument:** One or more sections (e.g., consent statement, content questions only)
- **Draft questions:** An unstructured list of questions for early-stage feedback
- **Description:** User describes the instrument rather than pasting it

If invoked with `$ARGUMENTS`, treat that as the instrument content to review.

If no instrument is provided, prompt the user to supply one.

### Step 2: Classify the Instrument

Before scoring, identify the instrument type (Household Survey, Self-Administered Survey, KII Guide, FGD Guide, Exit Survey, Rapid Assessment Tool, Registration/Intake Form). State the classification explicitly and adjust expectations:
- **KII/FGD Guides:** Apply Sections 1, 3, and 5 fully. Note that Sections 2 and 4 have qualitative-specific standards (open-ended flow, purposive sampling)
- **Exit Surveys:** Emphasize Sections 2, 3, and 5; note length feasibility is critical
- **Partial / Draft:** Review what is present; flag structural gaps as "needs development" rather than FAIL

### Step 3: Handle Non-Standard Input

**Question list without structure:** If only a list of questions is provided (no intro, no consent, no demographics), apply Section 3 in full. Note that Sections 1, 2, 5, and 6 cannot be assessed without seeing the full instrument.

**Narrative description:** If the user describes the instrument rather than pasting it, summarize your understanding first, then apply the review. Flag sections the description did not address as "not confirmed present."

**Multiple-language instrument:** If the instrument appears to be a translation, note any questions that may have introduced bias or ambiguity in translation. Apply the same scoring standards.

### Step 4: Conduct 6-Section Review

Review in this sequence, scoring each section PASS / PARTIAL / FAIL:

1. **Purpose and Logframe Alignment** — Purpose stated? Questions map to indicators or evaluation questions? Survey scope proportionate?
2. **Instrument Structure and Flow** — Standard components present (intro, consent, demographics, content, wrap-up)? Skip logic marked? Topics sequenced logically?
3. **Question Quality** — Neutral and non-leading? Single-concept per question? Response formats balanced and exhaustive? Recall periods defined?
4. **Sampling and Coverage** — Population defined? Sampling method stated? Sample size with rationale? Disaggregation dimensions collected?
5. **Ethical Compliance** — Informed consent present? Voluntary participation stated? Confidentiality addressed? Sensitive topic safeguards present?
6. **Practical Feasibility** — Instrument length appropriate? Enumerator instructions present? Pre-testing noted or planned?

### Step 5: Calculate Overall Rating

- **Strong:** 0 FAIL, max 1 PARTIAL
- **Adequate:** 0 FAIL, 2+ PARTIAL
- **Needs Revision:** 1 FAIL, or 3+ PARTIAL
- **Major Issues:** 2+ FAIL

**Note:** A FAIL in Ethical Compliance automatically triggers Major Issues regardless of other scores.

### Step 6: Generate Output

```
## Survey Instrument Review Summary

**Instrument Type:** [Classified type]
**Overall Rating:** [Strong / Adequate / Needs Revision / Major Issues]

**Score Summary:**
| Section | Score |
|---------|-------|
| 1. Purpose and Logframe Alignment | PASS / PARTIAL / FAIL |
| 2. Instrument Structure and Flow | PASS / PARTIAL / FAIL |
| 3. Question Quality | PASS / PARTIAL / FAIL |
| 4. Sampling and Coverage | PASS / PARTIAL / FAIL |
| 5. Ethical Compliance | PASS / PARTIAL / FAIL |
| 6. Practical Feasibility | PASS / PARTIAL / FAIL |

---

## Priority Recommendations

[3-5 highest-priority issues, ordered by severity. Lead with the specific finding, then the recommendation. Cite the question number where applicable.]

1. **[Section Name — Question #X if applicable]:** [Specific finding] — [Specific recommendation]
2. ...

---

## Detailed Findings

### 1. Purpose and Logframe Alignment — [PASS / PARTIAL / FAIL]
[Findings]

### 2. Instrument Structure and Flow — [PASS / PARTIAL / FAIL]
[Findings — note which standard components are present/missing]

### 3. Question Quality — [PASS / PARTIAL / FAIL]
[Findings — list specific problematic questions by number with the issue type (leading, double-barreled, undefined recall, etc.)]

### 4. Sampling and Coverage — [PASS / PARTIAL / FAIL]
[Findings — note "qualitative purposive sampling" standards apply for KII/FGD]

### 5. Ethical Compliance — [PASS / PARTIAL / FAIL]
[Findings — flag any elevated-risk topics that require additional safeguards]

### 6. Practical Feasibility — [PASS / PARTIAL / FAIL]
[Findings — estimate instrument length if possible]

---

## Design Flaw Flags
[List any common design flaws detected, with the relevant section reference. E.g., "Topic bloat (Section 1) — 15 questions not linked to any stated indicator."]
```

## Output Rules

- For question quality issues, cite the specific question number and quote the problematic text
- Flag ethical concerns first in Priority Recommendations if a FAIL is present
- For KII/FGD guides, do not penalize for absence of structured response options — open-ended is the standard
- Do not suggest shortening an instrument without identifying which questions are lower priority
- When a question appears to be a validated standard indicator, note it should not be reworded
