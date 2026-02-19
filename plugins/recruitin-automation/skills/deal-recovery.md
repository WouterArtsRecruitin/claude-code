# Skill: Deal Recovery

## Purpose
Diagnose stalled or at-risk deals and generate recovery strategies.

## Activation
Auto-activated when `{{OPERATION_TYPE}}` is: `deal_rescue`, `crisis_management`

## Risk Detection Criteria

### Automatic Risk Flags
| Signal | Risk Level | Trigger |
|--------|-----------|---------|
| No activity >7 days (S2) | Medium | Auto-flag |
| No activity >5 days (S3/S4) | High | Auto-flag |
| Client cancelled meeting | High | Manual/Zapier trigger |
| Candidate withdrew | Critical | Manual/Zapier trigger |
| Competitor mentioned | Medium | Manual flag |
| Budget freeze communicated | Critical | Manual flag |
| Contact person changed | High | Pipedrive trigger |
| Multiple rescheduled meetings | Medium | Activity pattern |

### Risk Score Calculation
```
RISK_SCORE = (
  days_stalled / stage_sla * 30 +          # How overdue (max 30)
  missed_touchpoints * 10 +                 # Communication gaps (max 30)
  negative_signals * 15 +                   # Bad signs (max 30)
  (1 - engagement_rate) * 10               # Low engagement (max 10)
)
# Cap at 100
```

## Recovery Playbooks

### Playbook A: Ghosting (no response)
1. **Day 0:** Different channel attempt (email → LinkedIn → phone)
2. **Day 2:** Value-add message (market insight, no ask)
3. **Day 5:** Direct question ("Should I interpret silence as...?")
4. **Day 8:** Final reach-out with clear exit
5. **Day 10:** Close deal as "No response", set 30-day re-engagement reminder

### Playbook B: Stalled Process (engaged but not moving)
1. Identify blocker: internal approval? competing priorities? uncertainty?
2. Offer to help remove blocker (provide ROI data, reference calls, etc.)
3. Create artificial urgency (candidate availability, market timing)
4. Propose modified timeline or scope to reduce commitment barrier
5. If blocked >14 days: executive-level outreach

### Playbook C: Competitor Threat
1. Assess competitive position (our strengths vs competitor)
2. Reinforce unique value without badmouthing
3. Accelerate timeline if possible
4. Add exclusivity element (priority candidate access, extended guarantee)
5. Prepare for loss: document learnings, maintain relationship

### Playbook D: Candidate Risk
1. Identify cause: counter-offer, cold feet, better opportunity, personal
2. For counter-offer: prepare "why leave" reinforcement, long-term view
3. For cold feet: additional information, meet the team, address concerns
4. For competing offer: accelerate, improve terms if possible
5. For personal: respect, maintain relationship, have backup candidate ready

### Playbook E: Budget/Freeze
1. Acknowledge situation empathetically
2. Offer modified engagement (retained vs contingent, phased approach)
3. Maintain relationship for when freeze lifts
4. Set calendar reminder for quarterly check-in
5. Redirect resources to active opportunities

## Output Format
Each recovery plan must include:
- **Diagnosis:** What went wrong and why
- **Strategy:** Which playbook and adaptations
- **Timeline:** Day-by-day action plan
- **Templates:** Ready-to-send messages for each step
- **Exit Criteria:** When to stop trying
- **Learnings:** What to change for future deals
