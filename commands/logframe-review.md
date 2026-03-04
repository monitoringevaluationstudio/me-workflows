---
description: Review a logframe or results framework for structural completeness, vertical/horizontal logic, assumptions, indicator quality, and strategic coherence
argument-hint: "[paste your logframe or describe the program]"
---

# /logframe-review -- Logframe Review

Review a logframe or results framework against established M&E standards. Produces a scored review across 7 dimensions with prioritized recommendations and a detailed findings table.

## Invocation

```
/me-workflows:logframe-review

[paste your logframe here]
```

## Workflow

### Step 1: Accept Input

Accept the logframe in any of these formats:
- **Table or matrix:** Standard logframe grid with columns and rows
- **Pasted text:** Narrative description of the results framework
- **Document extract:** Sections from a proposal or design document
- **Two versions:** Original and revised logframe for comparison review

If invoked with `$ARGUMENTS`, treat that as the logframe content to review.

If no logframe is provided, prompt the user to supply one.

### Step 2: Handle Non-Standard Input

**Partial logframes:** If only some components are provided (e.g., indicators without assumptions):
1. Note which components are present and which are missing
2. Apply all checks possible with available data
3. For missing components, state what cannot be assessed
4. Score each section — use PARTIAL or FAIL with "insufficient data" where needed

**Non-standard terminology:** Map donor-specific terms to standard hierarchy before reviewing (see skill methodology for mapping table).

**Narrative description:** If the user describes a logframe rather than pasting it (e.g., "My logframe has 2 outcomes and 5 outputs..."), first reconstruct what you understand as a brief parsed table, then apply the review. Flag any sections where the description was silent as "not confirmed present" rather than "missing" — the actual document may contain it.

**Version comparison:** If two versions are provided, compare section by section, noting improvements and remaining issues.

**Non-text input:** If the user provides an image or screenshot, ask them to paste the content as text or table.

### Step 3: Conduct 7-Section Review

Review in this sequence, scoring each section PASS / PARTIAL / FAIL:

1. **Structural Completeness** — Four standard columns present? Results hierarchy complete? No levels skipped?
2. **Vertical Logic** — IF-THEN causal chain plausible from activities to goal? Logic gaps?
3. **Horizontal Logic** — Indicators measure stated results? Data sources named? Targets with baselines? Disaggregation?
4. **Assumptions** — External factors only? Stated as positive conditions? Critical assumptions flagged?
5. **Indicator Quality** — Rapid SMART check. Flag indicators failing 2+ criteria. (For full indicator assessment, refer to `/me-workflows:indicator-quality`)
6. **Strategic Considerations** — Theory of Change alignment? Cross-cutting themes? Sustainability?
7. **Common Design Flaws** — Outputs-as-activities? Too many indicators? Missing baselines? Circular logic? (Fold findings into relevant scored sections)

### Step 4: Calculate Overall Rating

Based on section scores:
- **Strong:** 0 FAIL, max 1 PARTIAL
- **Adequate:** 0 FAIL, 2+ PARTIAL
- **Needs Revision:** 1 FAIL, or 3+ PARTIAL
- **Major Issues:** 2+ FAIL

**Note:** A FAIL in Structural Completeness or Vertical Logic automatically triggers Major Issues regardless of other scores. For EU logframes, do not penalize pre-conditions at the activity level — these are a convention (not a flaw) and should not trigger a FAIL in Assumptions.

### Step 5: Generate Output

Produce the structured review with summary, section scores, priority recommendations, and detailed findings table.

## Output Format

```
## Logframe Review Summary

**Overall Rating:** [Strong / Adequate / Needs Revision / Major Issues]

### Structural Completeness: [PASS / PARTIAL / FAIL]
[Findings]

### Vertical Logic: [PASS / PARTIAL / FAIL]
[Findings — identify specific logic gaps]

### Horizontal Logic: [PASS / PARTIAL / FAIL]
[Findings — identify measurement weaknesses]

### Assumptions: [PASS / PARTIAL / FAIL]
[Findings — identify missing or internal assumptions]

### Indicator Quality: [PASS / PARTIAL / FAIL]
[Findings — flag weak indicators]

### Strategic Considerations: [PASS / PARTIAL / FAIL]
[Findings — ToC alignment, cross-cutting themes, sustainability]

### Priority Recommendations (max 5)
1. [Most critical issue]
2. [Second priority]
3. [Third priority]
(Additional findings in the Detailed Findings Table below)

### Detailed Findings Table
| Level | Result | Issue | Severity | Recommendation |
|-------|--------|-------|----------|----------------|
| ... | ... | ... | High/Med/Low | ... |
```

## Notes

- Be specific. "Indicators need improvement" is not useful. "Output 2.1 indicator measures activities not outputs" is useful.
- Distinguish between structural issues (wrong format) and substantive issues (wrong logic).
- If the logframe is generally strong, say so — don't manufacture problems.
- If critical information is missing, flag it but don't assume the worst.
- A logframe is iterative — frame recommendations as improvements, not failures.
