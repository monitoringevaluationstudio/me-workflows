---
description: Review an M&E plan, MEAL plan, PMP, or indicator framework for completeness, indicator quality, data collection feasibility, roles, reporting, and quality assurance
argument-hint: "[paste your M&E plan or describe the plan structure]"
---

# /me-plan-review -- M&E Plan Review

Review a monitoring and evaluation plan against operational M&E standards. Produces a scored review across 8 dimensions with prioritized recommendations.

## Invocation

```
/me-workflows:me-plan-review

[paste your M&E plan here]
```

## Workflow

### Step 1: Accept Input

Accept the M&E plan in any of these formats:
- **Full document:** Complete M&E or MEAL plan pasted as text or table
- **Sections:** Individual sections (indicator table, data collection matrix, reporting schedule)
- **Narrative description:** User describes the plan rather than pasting it
- **Partial draft:** Incomplete plan for early-stage feedback

If invoked with `$ARGUMENTS`, treat that as the plan content to review.

If no plan content is provided, prompt the user to supply one.

### Step 2: Classify the Document

Before scoring, identify the document type (Full M&E Plan, PMP, Indicator Framework, MEL Plan, Data Management Plan, M&E Framework, or Partial Draft). State the classification explicitly at the top of the review and adjust expectations accordingly:
- **Indicator Frameworks:** Score only Sections 2 and 3 in full; note Sections 4-7 are out of scope
- **Data Management Plans:** Focus on Sections 3 and 6; skip evaluation-only sections
- **Partial Drafts:** Note gaps as "needs development" rather than FAIL for intentionally omitted sections

### Step 3: Handle Non-Standard Input

**Narrative description:** If the user describes the plan rather than pasting it, first summarize your understanding of each section, then apply the review. Flag any sections the description did not address as "not confirmed present."

**Indicator tables only:** If only an indicator list is provided, apply Section 2 in full and Section 3 partially. Note that Sections 4-8 cannot be assessed without the full plan.

**Multi-language or translated content:** Apply the same standards. Note if non-standard terminology appears to be a translation artifact.

### Step 4: Conduct 8-Section Review

Review in this sequence, scoring each section PASS / PARTIAL / FAIL:

1. **Structural Completeness** — All standard components present? Covers full M&E cycle?
2. **Indicator Framework Quality** — Indicators at all result levels? Each with source, baseline, target, disaggregation? For deep per-indicator scoring, refer to `/me-workflows:indicator-quality`
3. **Data Collection Plan** — Methods per indicator? Tools named? Frequency and sampling defined? Responsibility assigned?
4. **Roles, Responsibilities, and Capacity** — Responsibilities distributed beyond M&E staff? Supervision assigned? Capacity addressed?
5. **Reporting Framework** — Frequency, formats, and audiences defined? Learning and feedback loops included?
6. **Quality Assurance** — DQA protocol present? Verification steps described? Ongoing, not one-time?
7. **Evaluation Planning** — Evaluation type and questions stated? Linked to decision points? Budget indicated?
8. **Internal Consistency** — Do indicators, methods, roles, and reporting frequency align? Any contradictions?

### Step 5: Calculate Overall Rating

- **Strong:** 0 FAIL, max 1 PARTIAL
- **Adequate:** 0 FAIL, 2+ PARTIAL
- **Needs Revision:** 1 FAIL, or 3+ PARTIAL
- **Major Issues:** 2+ FAIL

**Note:** A FAIL in Structural Completeness or Indicator Framework automatically triggers Major Issues regardless of other scores.

### Step 6: Generate Output

```
## M&E Plan Review Summary

**Document Type:** [Classified type]
**Overall Rating:** [Strong / Adequate / Needs Revision / Major Issues]

**Score Summary:**
| Section | Score |
|---------|-------|
| 1. Structural Completeness | PASS / PARTIAL / FAIL |
| 2. Indicator Framework Quality | PASS / PARTIAL / FAIL |
| 3. Data Collection Plan | PASS / PARTIAL / FAIL |
| 4. Roles, Responsibilities & Capacity | PASS / PARTIAL / FAIL |
| 5. Reporting Framework | PASS / PARTIAL / FAIL |
| 6. Quality Assurance | PASS / PARTIAL / FAIL |
| 7. Evaluation Planning | PASS / PARTIAL / FAIL |
| 8. Internal Consistency | PASS / PARTIAL / FAIL |

---

## Priority Recommendations

[3-5 highest-priority issues, ordered by severity. Lead with the specific finding, then the recommendation. No generic advice.]

1. **[Section Name]:** [Specific finding] — [Specific recommendation]
2. ...

---

## Detailed Findings

### 1. Structural Completeness — [PASS / PARTIAL / FAIL]
[Findings]

### 2. Indicator Framework Quality — [PASS / PARTIAL / FAIL]
[Findings — note if full per-indicator assessment is needed via `/me-workflows:indicator-quality`]

### 3. Data Collection Plan — [PASS / PARTIAL / FAIL]
[Findings]

### 4. Roles, Responsibilities & Capacity — [PASS / PARTIAL / FAIL]
[Findings]

### 5. Reporting Framework — [PASS / PARTIAL / FAIL]
[Findings]

### 6. Quality Assurance — [PASS / PARTIAL / FAIL]
[Findings]

### 7. Evaluation Planning — [PASS / PARTIAL / FAIL]
[Findings — note "Out of scope for this document type" if applicable]

### 8. Internal Consistency — [PASS / PARTIAL / FAIL]
[List any cross-section contradictions found]

---

## Design Flaw Flags
[List any common design flaws detected, folded into the relevant sections above. E.g., "M&E staff as sole owners (Section 4), Reporting upward only (Section 5)"]
```

## Output Rules

- Lead each finding with the specific gap or issue, not a generic category label
- Cite MEAL rules where they directly support a finding
- For PARTIAL scores, state exactly what is present and what is missing
- For narrative/incomplete inputs, distinguish between "not present" and "not confirmed present"
- Do not recommend using `/me-workflows:indicator-quality` more than once (Section 2 is sufficient)
