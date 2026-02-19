# /pipeline-report — Pipeline Analysis Command

Generate comprehensive pipeline analysis with forecasting.

## Trigger
`/pipeline-report` or `/pipeline-report [period]` where period is:
- `weekly` (default)
- `monthly`
- `quarterly`

## Variables (auto-set)
```
{{OPERATION_TYPE}} = "pipeline_report"
{{URGENCY}} = "this_week"
{{OUTPUT_AUDIENCE}} = "internal"
{{INTEGRATION_TARGET}} = "pipedrive"
```

## Analysis Framework

### Pipeline Health Metrics
1. **Velocity:** Average days per stage transition
2. **Conversion:** % deals moving forward per stage
3. **Volume:** Total deals and value per stage
4. **Aging:** Deals exceeding stage SLA
5. **Win Rate:** Closed-won vs total closed
6. **Revenue Forecast:** Weighted pipeline (value * probability per stage)

### Stage Probability Weights
| Stage | Probability | SLA (days) |
|-------|------------|------------|
| Stage 1 — Qualification | 10% | 5 |
| Stage 2 — Engagement | 25% | 10 |
| Stage 3 — Proposal/Interview | 50% | 14 |
| Stage 4 — Negotiation | 75% | 7 |
| Stage 5 — Closing | 90% | 5 |

### Forecasting Model
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
S1 → S2: X% | S2 → S3: X% | S3 → S4: X% | S4 → S5: X% | S5 → Won: X%

### Attention Required
1. [Deal/Issue] — [Why] — [Recommended action]
2. ...

### Wins This Period
- [Deal] — €[Value] — [Notable detail]

### Trends
- [Trend observation 1]
- [Trend observation 2]
- [Comparison to previous period]
```
