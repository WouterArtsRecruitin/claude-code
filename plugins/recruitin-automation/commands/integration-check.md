---
description: Verify integration health between Pipedrive, Zapier, Jotform, and other tools
argument-hint: "Optional: pipedrive, zapier, jotform, email, slack, or all"
---

# Integration Health Check

You are checking the health of RecruitIn's tool integrations. Verify connections, identify issues, and suggest fixes.

## Context

- MCP config: `plugins/recruitin-automation/.mcp.json` for live API access
- Pipeline reference: `plugins/recruitin-automation/knowledge/pipeline-stages.md`

## Variables
- OPERATION_TYPE: integration_check
- URGENCY: asap
- OUTPUT_AUDIENCE: internal
- INTEGRATION_TARGET: all (or as specified)

## Integration Map
```
Jotform (intake) → Zapier (routing) → Pipedrive (CRM)
                                    → Email (notifications)
                                    → Slack (alerts)

Pipedrive (stage change) → Zapier (trigger) → Email (templates)
                                             → Slack (updates)
                                             → Jotform (feedback)

LinkedIn (manual) → Pipedrive (log activity)
```

## Health Check Points
For each integration, verify:
1. **Connection:** Is the API connection active?
2. **Last Sync:** When was data last transferred?
3. **Error Log:** Any failed triggers in last 24h?
4. **Data Integrity:** Are fields mapping correctly?
5. **Rate Limits:** Are we approaching API limits?

## Common Issues & Fixes
| Issue | Symptom | Fix |
|-------|---------|-----|
| Zapier trigger missed | Deal changed but no email | Check Zap ON, verify triggers |
| Jotform incomplete | Missing Pipedrive fields | Check field mapping |
| Pipedrive sync lag | Old data showing | Check rate limits, webhooks |
| Email bounce | Not delivered | Check DKIM/SPF |
| Duplicates | Same lead twice | Check Zapier dedup filter |

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
1. **[SEVERITY]** [Integration] — [Issue]
   - **Impact:** [affected]
   - **Fix:** [steps]
   - **Prevention:** [avoid recurrence]

### All Clear?
"All integrations operational. Next check: [date]."
```

Note: With MCP configured (`.mcp.json`), this performs live API checks. Without MCP, generates a manual check template.
