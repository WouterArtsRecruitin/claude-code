# Skill: Pipeline Management

## Purpose
Monitor, analyze, and optimize the recruitment pipeline across all stages.

## Activation
Auto-activated when `{{OPERATION_TYPE}}` is: `daily_routine`, `deal_rescue`, `pipeline_report`, `integration_check`, `strategic_planning`, `crisis_management`

## Pipeline Stage Definitions

### RecruitIn Standard Pipeline
| Stage | Name | Description | SLA | Probability |
|-------|------|-------------|-----|-------------|
| S1 | Qualification | New lead, needs assessment | 5 days | 10% |
| S2 | Engagement | Active communication, building relationship | 10 days | 25% |
| S3 | Proposal/Interview | Formal process, candidate presentation | 14 days | 50% |
| S4 | Negotiation | Terms discussion, offer stage | 7 days | 75% |
| S5 | Closing | Final agreement, contract signing | 5 days | 90% |

### Stage Transition Rules
- Forward movement: always allowed
- Backward movement: flag as regression, require reason
- Skip stages: flag as anomaly, verify data integrity
- SLA breach: auto-flag as "attention needed"

## Key Metrics

### Health Indicators
```
Pipeline Velocity = Σ(deal_value * stage_probability) / avg_cycle_days
Conversion Rate[stage] = deals_moved_forward / total_deals_at_stage
Stage Aging = current_date - stage_entry_date
Win Rate = closed_won / (closed_won + closed_lost)
Pipeline Coverage = weighted_pipeline / revenue_target
```

### Thresholds
| Metric | Green | Yellow | Red |
|--------|-------|--------|-----|
| Pipeline Coverage | >3x target | 2-3x target | <2x target |
| Avg Conversion | >30% per stage | 20-30% | <20% |
| SLA Compliance | >80% | 60-80% | <60% |
| Win Rate | >25% | 15-25% | <15% |

## Actions Library
- **Pipeline is thin** → activate lead generation, increase outreach volume
- **Stage 2 bottleneck** → review engagement approach, check response rates
- **Stage 3 bottleneck** → improve proposal quality, prep candidates better
- **Stage 4 stalling** → review negotiation approach, check market rates
- **Low win rate** → qualify harder at S1, improve candidate matching
- **High pipeline, low close** → focus on conversion, reduce new intake temporarily
