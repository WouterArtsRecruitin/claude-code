---
description: Quarterly strategic planning — forecasting, market analysis, resource allocation, growth roadmap
argument-hint: "Optional: Q1, Q2, Q3, Q4, or specific focus area"
---

# Strategic Planning

You are generating a strategic recruitment plan for RecruitIn. Provide deep analysis with scenarios, market context, and actionable roadmap.

## Context

- Pipeline state: `plugins/recruitin-automation/workflows/current-state.md`
- Pipeline management: `plugins/recruitin-automation/skills/pipeline-management.md`
- Market analysis: `plugins/recruitin-automation/skills/market-analysis.md`
- Lead scoring: `plugins/recruitin-automation/skills/lead-scoring.md`

## Variables
- OPERATION_TYPE: strategic_planning
- URGENCY: strategic
- OUTPUT_AUDIENCE: internal
- COMPLIANCE_LEVEL: standard

## Analysis Framework

### 1. Current State Assessment
- Pipeline health summary (use pipeline-management skill)
- Win rate trend (improving/stable/declining)
- Revenue vs target
- Team capacity and utilization

### 2. Market Context
- Sector demand trends (use market-analysis skill)
- Salary movement direction
- Competitor activity
- Regulatory changes

### 3. Scenario Planning
For each scenario, model:
- **Best case:** assumptions, projected revenue, required actions
- **Expected case:** assumptions, projected revenue, required actions
- **Worst case:** assumptions, projected revenue, required actions

### 4. Growth Levers
Rank by impact and effort:
- Client acquisition (new business development)
- Client expansion (more roles from existing clients)
- Candidate pool growth (sourcing investment)
- Process improvement (faster time-to-fill)
- Fee optimization (pricing strategy)

### 5. Resource Allocation
- Where to focus recruiter time this quarter
- Budget allocation across channels
- Tool/technology investments needed
- Training or capability gaps

### 6. Risk Mitigation
- Top 3 business risks this quarter
- Mitigation strategy for each
- Early warning indicators to monitor

## Output Format
```markdown
## Strategic Plan — [QUARTER/YEAR]

### Executive Summary
[3-5 sentences: where we are, where we're going, what it takes]

### Current Position
- Pipeline: €[X] total | [Y] deals | Win rate: [Z]%
- Revenue YTD: €[X] vs target €[Y] ([Z]% of target)
- Team: [X] recruiters | [Y] deals per recruiter

### Market Outlook
[2-3 key trends with confidence levels]

### Scenarios
| | Best | Expected | Worst |
|---|---|---|---|
| Revenue | €X | €X | €X |
| New clients | X | X | X |
| Placements | X | X | X |
| Probability | X% | X% | X% |

### Strategic Priorities (ranked)
1. [Priority] — Expected impact: €[X] — Effort: [Low/Med/High]
2. [Priority] — Expected impact: €[X] — Effort: [Low/Med/High]
3. [Priority] — Expected impact: €[X] — Effort: [Low/Med/High]

### Action Plan
| Week | Action | Owner | Metric |
|------|--------|-------|--------|
| 1-2 | [Action] | [Who] | [How measured] |
| 3-4 | [Action] | [Who] | [How measured] |
| ... | ... | ... | ... |

### Risks & Mitigation
| Risk | Likelihood | Impact | Mitigation | Early Warning |
|------|-----------|--------|------------|---------------|
| [Risk] | [H/M/L] | [H/M/L] | [Strategy] | [Indicator] |

### Review Schedule
- Monthly pipeline review: [dates]
- Mid-quarter strategy check: [date]
- Quarter-end retrospective: [date]
```

## Approval
Strategic plans require full review cycle: Draft → Review → Iterate → Approve. Present draft and wait for feedback before finalizing.
