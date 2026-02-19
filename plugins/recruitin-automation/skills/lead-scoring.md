# Skill: Lead Scoring

## Purpose
Score and prioritize both client leads (companies) and candidate leads using recruitment-specific criteria.

## Activation
Auto-activated when `{{OPERATION_TYPE}}` is: `daily_routine`, `lead_scoring`, `strategic_planning`

## Scoring Models

### Client Lead Score (CLS)
```
CLS = (
  company_size_score * 0.20 +
  hiring_urgency_score * 0.25 +
  budget_clarity_score * 0.15 +
  role_difficulty_score * 0.15 +
  relationship_warmth_score * 0.15 +
  market_demand_score * 0.10
) * 10
```

### Candidate Lead Score (CALS)
```
CALS = (
  availability_score * 0.25 +
  skill_match_score * 0.25 +
  salary_alignment_score * 0.20 +
  interview_readiness_score * 0.15 +
  cultural_fit_score * 0.15
) * 10
```

### Score to Action Mapping
| Score | Label | Action | Timeline |
|-------|-------|--------|----------|
| 80-100 | HOT | Personal outreach, fast-track | Today |
| 60-79 | WARM | Schedule contact | Within 48h |
| 40-59 | NURTURE | Add to drip sequence | Weekly check |
| 20-39 | COLD | Low-touch monitoring | Monthly review |
| 0-19 | ARCHIVE | No active pursuit | Quarterly re-eval |

## Data Requirements
- Minimum: name + type (client/candidate) + 2 scoring factors
- Optimal: all scoring factors + historical interaction data
- If data insufficient: output partial score with "[INCOMPLETE — missing: X, Y]" flag

## Integration
- Pipedrive: map score to custom field "Lead Score", update deal label
- Zapier: trigger different sequences based on score bracket
- Email: auto-select template based on score bracket
