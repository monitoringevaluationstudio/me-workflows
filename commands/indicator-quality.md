---
description: Assess a set of indicators against SMART/CREAM frameworks, check disaggregation, validate data sources, and produce a prioritized scorecard with revision recommendations
argument-hint: "[paste your indicators or describe what you're measuring]"
---

# /indicator-quality -- Indicator Quality Assessment

Assess indicators against established quality frameworks. Produces a scorecard with SMART scores, disaggregation checks, data source validation, and priority recommendations.

## Invocation

```
/me-workflows:indicator-quality

[paste indicators here]
```

## Workflow

### Step 1: Accept Input

Accept indicators in any of these formats:
- **List or table:** Indicator names with optional targets, baselines, data sources
- **CSV or spreadsheet data:** Parse columns (common headers: Indicator, Target, Actual, Baseline, Data Source, Frequency, Disaggregation)
- **Logframe extract:** Extract indicators from the logframe and assess them, referencing the result level they measure
- **Indicator reference sheet:** Full IRS with metadata
- **Description:** User describes what they want to measure — help develop quality indicators

If invoked with `$ARGUMENTS`, treat that as the indicator content to assess.

If no indicators are provided, prompt the user to supply them.

### Step 2: Classify Input

Before assessing, verify the input actually contains indicators. Users sometimes provide:

- **Templates or checklists about indicators** — These are meta-documents, not indicators. Inform the user and offer to assess any actual indicators embedded within, or help them develop indicators.
- **Evaluation questions** — Redirect to `/me-workflows:tor-review`.
- **Activity descriptions** — "Conduct 5 trainings" is an activity, not an indicator. Help the user formulate indicators that measure the activity's result.

### Step 3: Parse Indicators

Extract each indicator and identify:
- The indicator statement
- Which result level it measures (output, outcome, impact) — infer from context if not stated
- Any existing targets, baselines, or data sources
- Whether it's quantitative or qualitative

Flag result-level mismatches (e.g., an activity count labeled as an outcome indicator).

### Step 4: Assess Each Indicator

For each indicator, apply these checks in sequence:

1. **SMART Score** — Score each of the 5 dimensions (1-5 scale) using the anchor scales from the skill methodology. Calculate composite score (average of scored dimensions, excluding N/A).
2. **Disaggregation Check** — Are minimum dimensions specified (sex, age, geography)? Flag as a cross-cutting finding if no disaggregation is mentioned anywhere.
3. **Data Source Validation** — Is the data source named, accessible, and consistent? Baseline planned?
4. **Formulation Check** — Check for double-barreled, process-as-outcome, undefined terms, missing units, unclear denominators.
5. **Standard Indicator Check** — Note if validated standard indicators exist for the sector. For recognized standard indicators (WHO, SDG, Global Fund, Sphere), do not recommend rewording — assess usage and compliance instead.

### Step 5: Assess Set Coverage (for 5+ indicators)

Check whether the full set tells a coherent measurement story: result-level balance, activity-count dominance, outcome gaps, denominator availability.

### Step 6: Generate Output

**Scale response to set size:**
- **Small sets (1-4 indicators):** Full detailed assessment for every indicator. Include a brief "Strengths" note for any indicator that scores 4.0+ on any dimension.
- **Medium sets (5-14 indicators):** Summary scorecard for all, then detailed assessment for any scoring below 3.0 or with critical formulation issues.
- **Large sets (15+ indicators):** Summary scorecard for all, then detailed assessment only for the 5-6 with the most significant issues. Group common findings.

### Handling Incomplete Input

Users often provide indicators without full context:

- **Indicators only (no targets/baselines):** Score Specific, Relevant, and formulation quality. Mark Achievable and Time-bound as N/A. Do NOT penalize for missing context that wasn't provided.
- **No disaggregation mentioned:** Flag once as cross-cutting finding, don't repeat per indicator.
- **No data sources provided:** Note as a gap to address — don't score every indicator as failing.
- **Sector context inference:** If the user doesn't state the sector but indicators suggest one (e.g., "ANC visits" = health), note the inferred sector. Helps calibrate standard indicator awareness and disaggregation expectations.

### Standard Donor Indicators

Some indicators are pre-defined by donors with fixed definitions. If you recognize standard indicators:
- Assess whether they are being used correctly (right result level, right target population)
- Check that disaggregation matches donor requirements
- Do NOT recommend rewording the indicator statement itself — flag it as a standard indicator

## Output Format

```
## Indicator Quality Assessment

**Indicators Reviewed:** [N]
**Overall Quality:** [Strong / Mixed / Needs Work]
**Data Completeness:** [What information was provided vs. what was missing]

### Summary Scorecard

| # | Indicator | SMART Score | Disagg | Data Source | Priority Issues |
|---|-----------|-------------|--------|-------------|-----------------|
| 1 | [name] | [X.X/5.0] | [Y/N/Not provided] | [Y/N/Not provided] | [key issue] |

### Cross-Cutting Findings
- [Patterns across multiple indicators — group common issues]
- [Systemic gaps in measurement approach]

### Detailed Assessment (top 5-6 issues)

#### Indicator [N]: [statement]
- **Result Level:** [Output/Outcome/Impact]
- **Strengths:** [what this indicator does well — required for any indicator scoring 4.0+ on any dimension; include even for weak indicators if one dimension is solid]
- **SMART Scores:**
  - S: [X/5] — [one-line rationale]
  - M: [X/5] — [one-line rationale]
  - A: [X/5 or N/A] — [one-line rationale or "no target provided"]
  - R: [X/5] — [one-line rationale]
  - T: [X/5 or N/A] — [one-line rationale or "no timeframe provided"]
  - **Composite: [X.X/5.0]** ([N] dimensions scored)
- **Issues:** [specific problems found]
- **Recommended Revision:** [improved indicator statement]

### Priority Recommendations
1. [Most impactful improvement]
2. [Second priority]
3. [Third priority]
```

## Notes

- Score based on what is provided. An indicator without a target in a CSV is not necessarily bad — the target may exist in a separate document.
- When suggesting revisions, keep them practical. A perfect indicator that can't be measured is worse than a good-enough one that can.
- Distinguish between formulation issues (fixable with rewording) and measurement feasibility issues (require budget/capacity).
- If no baseline exists, recommend establishing one — don't just flag it as a failure.
- Respect context: disaggregation by ethnicity may be inappropriate or dangerous in some settings.
- For deep logframe structural review beyond just indicators, use `/me-workflows:logframe-review`.
