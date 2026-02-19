# /daily-ops — Daily Operations Command

Run daily recruitment operations check: pipeline status, priority actions, follow-ups.

## Trigger
`/daily-ops` or `/daily-ops [focus_area]`

## Variables (auto-set)
```
{{OPERATION_TYPE}} = "daily_routine"
{{URGENCY}} = "this_week"
{{OUTPUT_AUDIENCE}} = "internal"
{{INTEGRATION_TARGET}} = "pipedrive"
```

## Execution Flow

1. **Pipeline Snapshot**
   - Pull current pipeline state from context or request it
   - Identify deals that changed stage in last 24h
   - Flag deals with no activity in >3 days

2. **Priority Actions**
   - Stage 2 deals needing follow-up (>48h since last contact)
   - Stage 3 deals approaching decision deadline
   - Stage 4 deals requiring contract preparation
   - New Stage 1 deals needing qualification

3. **Follow-up Queue**
   - Generate prioritized contact list
   - Include suggested action per contact (call/email/LinkedIn)
   - Flag any candidate resubmissions or client feedback pending

4. **Daily Metrics**
   - Deals moved forward vs backward
   - New deals added
   - Deals closed (won/lost)
   - Revenue pipeline delta

## Output Format
```markdown
## Daily Operations Report — [DATE]

### Pipeline Snapshot
[Current state summary]

### Priority Actions (do today)
1. [Action] — [Deal/Contact] — [Reason]
2. ...

### Follow-up Queue
| Priority | Contact | Company | Action | Last Activity |
|----------|---------|---------|--------|---------------|
| ...      | ...     | ...     | ...    | ...           |

### Metrics
- Deals forward: X | Deals back: Y
- New: X | Closed won: Y | Closed lost: Z
- Pipeline delta: +/- €X
```

## Error Handling
- If no pipeline data available: "[DATA NEEDED] Provide current Pipedrive export or describe pipeline state."
- If focus_area specified but not recognized: List available focus areas and proceed with full report.
