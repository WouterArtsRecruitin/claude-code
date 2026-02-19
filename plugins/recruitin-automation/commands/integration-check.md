# /integration-check — Integration Health Command

Verify and troubleshoot integrations between Pipedrive, Zapier, Jotform, and other tools.

## Trigger
`/integration-check` or `/integration-check [integration_name]`

## Variables (auto-set)
```
{{OPERATION_TYPE}} = "integration_check"
{{URGENCY}} = "asap"
{{OUTPUT_AUDIENCE}} = "internal"
{{INTEGRATION_TARGET}} = [all or specified]
```

## Integration Map

### Core Integrations
```
Jotform (intake) → Zapier (routing) → Pipedrive (CRM)
                                    → Email (notifications)
                                    → Slack (alerts)

Pipedrive (stage change) → Zapier (trigger) → Email (templates)
                                             → Slack (updates)
                                             → Jotform (feedback forms)

LinkedIn (manual) → Pipedrive (log activity)
```

### Health Check Points
For each integration, verify:
1. **Connection:** Is the API connection active?
2. **Last Sync:** When was data last transferred?
3. **Error Log:** Any failed triggers in last 24h?
4. **Data Integrity:** Are fields mapping correctly?
5. **Rate Limits:** Are we approaching API limits?

### Common Issues & Fixes
| Issue | Symptom | Fix |
|-------|---------|-----|
| Zapier trigger missed | Deal changed but no email sent | Check Zap is ON, verify trigger conditions |
| Jotform data incomplete | Missing fields in Pipedrive | Check field mapping, verify required fields |
| Pipedrive sync lag | Old data showing | Check API rate limits, verify webhook status |
| Email bounce | Templates not delivered | Check sender domain, verify DKIM/SPF |
| Duplicate records | Same lead entered twice | Check dedup rules in Zapier filter |

## Output Format
```markdown
## Integration Health Check — [DATE]

### Status Overview
| Integration | Status | Last Sync | Errors (24h) |
|------------|--------|-----------|--------------|
| Pipedrive  | OK/WARN/ERROR | [time] | [count] |
| Zapier     | OK/WARN/ERROR | [time] | [count] |
| Jotform    | OK/WARN/ERROR | [time] | [count] |
| Email      | OK/WARN/ERROR | [time] | [count] |
| Slack      | OK/WARN/ERROR | [time] | [count] |

### Issues Found
1. **[SEVERITY]** [Integration] — [Issue description]
   - **Impact:** [What's affected]
   - **Fix:** [Step-by-step resolution]
   - **Prevention:** [How to avoid recurrence]

### Recommendations
- [Optimization suggestion 1]
- [Optimization suggestion 2]

### No Issues?
If all integrations healthy: "All integrations operational. Next scheduled check: [date]."
```
