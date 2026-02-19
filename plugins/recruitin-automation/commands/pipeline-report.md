---
description: Comprehensive pipeline analysis with forecasting and trend detection
argument-hint: "Period: weekly (default), monthly, quarterly"
---

# Pipeline Report

You are generating a pipeline analysis report for RecruitIn. Provide metrics, forecasting, and actionable insights.

## Context

- Current state: `plugins/recruitin-automation/workflows/current-state.md`
- Pipeline definitions: `plugins/recruitin-automation/knowledge/pipeline-stages.md`
- Pipeline management: `plugins/recruitin-automation/skills/pipeline-management.md`
- Market context: `plugins/recruitin-automation/skills/market-analysis.md`

## Variables
- OPERATION_TYPE: pipeline_report
- URGENCY: this_week
- OUTPUT_AUDIENCE: internal
- INTEGRATION_TARGET: pipedrive

## Stage Probability Weights
| Stage | Probability | SLA (days) |
|-------|------------|------------|
| S1 — Qualification | 10% | 5 |
| S2 — Engagement | 25% | 10 |
| S3 — Proposal/Interview | 50% | 14 |
| S4 — Negotiation | 75% | 7 |
| S5 — Closing | 90% | 5 |

## Forecasting Model
- **Conservative:** Sum of (value * probability) for Stage 3+
- **Expected:** Sum of (value * probability) for all stages
- **Optimistic:** Sum of (value * probability * 1.2) for all stages

## Output Format
```markdown
## Pipeline Report — [PERIOD] — [DATE]

### Executive Summary
[2-3 sentence overview: total pipeline, direction, key concern]

### Pipeline Overview
| Stage | Deals | Value | Avg Age | SLA Status |
|-------|-------|-------|---------|------------|
| S1    | X     | €X    | X days  | OK/OVERDUE |
| S2    | X     | €X    | X days  | OK/OVERDUE |
| S3    | X     | €X    | X days  | OK/OVERDUE |
| S4    | X     | €X    | X days  | OK/OVERDUE |
| S5    | X     | €X    | X days  | OK/OVERDUE |
| **Total** | **X** | **€X** | | |

### Revenue Forecast
| Scenario | This Month | This Quarter |
|----------|-----------|--------------|
| Conservative | €X | €X |
| Expected | €X | €X |
| Optimistic | €X | €X |

### Conversion Funnel
S1→S2: X% | S2→S3: X% | S3→S4: X% | S4→S5: X% | S5→Won: X%

### Attention Required
1. [Deal/Issue] — [Why] — [Recommended action]

### Wins This Period
- [Deal] — €[Value] — [Notable detail]

### Trends
- [Trend 1]
- [Comparison to previous period]
```

After generating: update `plugins/recruitin-automation/workflows/current-state.md` with latest pipeline snapshot.
