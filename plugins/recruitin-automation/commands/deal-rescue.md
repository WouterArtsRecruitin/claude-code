# /deal-rescue — Deal Recovery Command

Analyze at-risk deals and generate recovery strategies.

## Trigger
`/deal-rescue` or `/deal-rescue [deal_name_or_id]`

## Variables (auto-set)
```
{{OPERATION_TYPE}} = "deal_rescue"
{{URGENCY}} = "asap"
{{OUTPUT_AUDIENCE}} = "internal"
{{INTEGRATION_TARGET}} = "pipedrive"
{{RISK_LEVEL}} = "high"
```

## Execution Flow

1. **Risk Assessment**
   - Identify deals with stalled progress (>7 days same stage)
   - Identify deals with negative signals (declined meetings, ghosting, competitor mentions)
   - Calculate risk score: days_stalled * stage_weight * value_factor

2. **Root Cause Analysis**
   For each at-risk deal, determine:
   - Is the bottleneck on candidate side, client side, or internal?
   - What was the last meaningful interaction?
   - Are there competing offers or alternative candidates?
   - Is timing/budget the issue?

3. **Recovery Strategy**
   For each deal, generate:
   - Immediate action (within 24h)
   - Follow-up sequence (3-touch plan)
   - Escalation trigger (when to involve senior/management)
   - Abandon criteria (when to cut losses)

4. **Communication Templates**
   Auto-generate for each recovery action:
   - Re-engagement email
   - Value reinforcement message
   - Urgency-creating follow-up
   - Graceful exit message (if abandon criteria met)

## Output Format
```markdown
## Deal Rescue Report — [DATE]

### At-Risk Deals (sorted by value)

#### [Deal Name] — €[Value] — Stage [X] — Risk: [HIGH/CRITICAL]
**Stalled:** [X] days | **Last contact:** [date] | **Bottleneck:** [candidate/client/internal]

**Root Cause:** [Analysis]

**Recovery Plan:**
1. [IMMEDIATE] [Action] — by [date]
2. [FOLLOW-UP 1] [Action] — by [date]
3. [FOLLOW-UP 2] [Action] — by [date]
4. [ESCALATION] If no response by [date] → [action]
5. [ABANDON] If [criteria] → close deal with reason: [reason]

**Draft Message:**
> Subject: [subject]
> [body]

---
[Repeat for each deal]

### Summary
- Deals at risk: [X] | Total value: €[Y]
- Recoverable (estimated): [X] deals | €[Y]
- Recommended abandons: [X] deals | €[Y]
```
