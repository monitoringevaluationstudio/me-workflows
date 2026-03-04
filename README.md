# M&E Workflows

Professional monitoring, evaluation, accountability and learning (MEAL) skills for Claude.

Paste a logframe, M&E plan, survey, evaluation TOR, or indicator list and get a structured quality review in seconds.

Built by [MEStudio](https://monitoringevaluationstudio.com).

---

> **Currently Mac only.** A known bug in Claude Desktop on Windows prevents automatic document detection. Windows support is coming.

---

## What It Does

| Skill | Use It When You Have... |
|-------|------------------------|
| `/me-workflows:logframe-review` | A logframe or results framework to check |
| `/me-workflows:indicator-quality` | A list of indicators to score against SMART criteria |
| `/me-workflows:tor-review` | An evaluation TOR or SOW to review |
| `/me-workflows:me-plan-review` | An M&E plan, MEAL plan, PMP, or MEL plan to assess |
| `/me-workflows:survey-review` | A survey, questionnaire, KII guide, or data collection instrument to check |

Each skill produces a scored review with section-by-section ratings (PASS / PARTIAL / FAIL), a summary verdict, and prioritized recommendations.

## Installation

### Claude Desktop (Mac)

1. Open Claude Desktop
2. Go to **Settings → Extensions**
3. Click **Add from GitHub** and enter: `monitoringevaluationstudio/me-workflows`
4. Click **Install**

That is it. No downloads, no coding, no setup.

### Claude Code (CLI)

```bash
claude mcp install monitoringevaluationstudio/me-workflows
```

## How to Use

Type a slash command, then paste your document:

**Logframe review:**
```
/me-workflows:logframe-review

Objective: Improved health outcomes for rural women
Output 1: 500 health workers trained
Output 2: 12 health facilities upgraded
Indicator: Number of women accessing services (target: 10,000)
```

**Indicator quality check:**
```
/me-workflows:indicator-quality

1. Number of health workers trained (target: 500)
2. % of facilities with adequate supplies (baseline: 42%)
3. Women's empowerment improved
```

**Evaluation TOR review:**
```
/me-workflows:tor-review

[paste your evaluation TOR here]
```

**M&E plan review:**
```
/me-workflows:me-plan-review

[paste your M&E plan, MEL plan, PMP, or MEAL plan here]
```

**Survey review:**
```
/me-workflows:survey-review

[paste your survey, questionnaire, or KII guide here]
```

Claude will review the document and return a structured report.

**On Mac:** You can also just paste a document without typing a command. Claude will detect what it is and apply the right review automatically.

## License

MIT — Copyright (c) 2026 MEStudio
