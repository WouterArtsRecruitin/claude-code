---
description: Emergency crisis response — hiring freezes, competitor threats, key client loss, market disruptions
argument-hint: "Describe the crisis situation"
---

# Crisis Response

You are executing an emergency crisis response protocol for RecruitIn. Assess impact, generate action plan, and prepare communications.

## Context

- Pipeline state: `plugins/recruitin-automation/workflows/current-state.md`
- Deal recovery: `plugins/recruitin-automation/skills/deal-recovery.md`
- Pipeline management: `plugins/recruitin-automation/skills/pipeline-management.md`
- Communication templates: `plugins/recruitin-automation/skills/communication-templates.md`
- Market analysis: `plugins/recruitin-automation/skills/market-analysis.md`

## Variables
- OPERATION_TYPE: crisis_management
- URGENCY: asap
- OUTPUT_AUDIENCE: internal
- RISK_LEVEL: critical

## Crisis Types

### Type A: Client Hiring Freeze
- Immediate: assess which deals are affected
- Quantify: total revenue at risk
- Act: pivot to unaffected clients, accelerate other deals
- Communicate: acknowledge to client, maintain relationship

### Type B: Competitor Threat
- Assess: which clients/candidates are at risk
- Differentiate: reinforce unique value
- Accelerate: fast-track deals in progress
- Defend: proactive outreach to at-risk relationships

### Type C: Key Client Loss
- Assess: revenue impact, pipeline dependency
- Diversify: redistribute effort to other clients
- Retain: attempt recovery if possible
- Replace: activate new business development

### Type D: Market Disruption
- Assess: sector-wide impact (layoffs, economic downturn, regulation)
- Adapt: pivot to resilient sectors
- Communicate: market insight content (position as expert)
- Prepare: scenario plan for duration of disruption

### Type E: Internal Crisis
- Team member departure, compliance issue, system failure
- Assess: immediate operational impact
- Stabilize: redistribute work, activate contingencies
- Communicate: transparent internal and external messaging

## Execution Protocol
1. **T+0 min:** Assess situation severity (1-10 scale)
2. **T+15 min:** Quantify financial impact on pipeline
3. **T+30 min:** Identify all affected deals and relationships
4. **T+1 hr:** Generate action plan with immediate + 7-day actions
5. **T+2 hr:** Prepare communication drafts (internal + external)
6. **T+4 hr:** Present plan for approval — NO AUTO-EXECUTE
7. **On approval:** Execute, set monitoring schedule

## Output Format
```markdown
## CRISIS RESPONSE — [DATE] — [TYPE]

### Severity: [X]/10

### Situation Assessment
[What happened, when, confirmed facts vs assumptions]

### Impact Analysis
- **Revenue at risk:** €[X]
- **Deals affected:** [X] deals | €[Y] value
- **Relationships at risk:** [list]
- **Timeline:** [How long will this last?]

### Immediate Actions (next 24h)
1. [Action] — [Who] — [By when]
2. [Action] — [Who] — [By when]
3. [Action] — [Who] — [By when]

### 7-Day Plan
| Day | Action | Owner | Expected Outcome |
|-----|--------|-------|-----------------|
| 1 | [Action] | [Who] | [Outcome] |
| 2-3 | [Action] | [Who] | [Outcome] |
| 4-5 | [Action] | [Who] | [Outcome] |
| 6-7 | [Action] | [Who] | [Outcome] |

### Communications
**Internal message:**
> [Draft]

**Client message (if applicable):**
> [Draft]

### Monitoring
- Daily check-in: [time]
- Escalation trigger: [condition]
- Resolution criteria: [when is crisis over?]
```

## CRITICAL: This command ALWAYS requires explicit approval before any action is taken. Never auto-execute crisis responses.
