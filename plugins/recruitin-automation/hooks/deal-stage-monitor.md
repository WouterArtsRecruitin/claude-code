# Hook: Deal Stage Monitor

## Purpose
Monitor deal stage changes and trigger alerts for regression or SLA breaches.

## Trigger
After any command that updates `workflows/current-state.md`

## Detection Rules

### Stage Regression Alert
If a deal moves backward (e.g., S3 → S2):
```
[REGRESSION ALERT] Deal "[name]" moved from Stage [X] to Stage [Y].
Reason needed. Consider running /deal-rescue for recovery analysis.
```

### SLA Breach Alert
If a deal exceeds stage SLA (from pipeline-stages.md):
- S1 > 5 days, S2 > 10 days, S3 > 14 days, S4 > 7 days, S5 > 5 days
```
[SLA BREACH] Deal "[name]" has been in Stage [X] for [Y] days (SLA: [Z] days).
Recommended: run /deal-rescue [deal_name]
```

### No-Activity Alert
If a deal has no activity logged in >3 business days:
```
[ACTIVITY NEEDED] Deal "[name]" — no activity for [X] days.
Suggested action: [call/email/meeting based on stage]
```

### Win/Loss Tracking
If a deal moves to Closed Won or Closed Lost:
```
[DEAL CLOSED — WON] "[name]" — €[value] — Congratulations!
  Time in pipeline: [X] days | Source: [source]

[DEAL CLOSED — LOST] "[name]" — €[value]
  Reason: [if available] | Stage at loss: [stage]
  Learning: [auto-suggest based on loss stage]
```

## Implementation Note
These hooks activate when `current-state.md` is updated by any command.
When MCP is configured with Pipedrive, these can also trigger on real-time webhook events.
Without MCP, monitoring is based on manual state updates.
