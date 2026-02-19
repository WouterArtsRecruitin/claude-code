# Error Handling & Fallback Strategy

## Error Categories

### Category 1: Missing Data
**Trigger:** Required variable or data point unavailable
**Response pattern:**
```
[DATA NEEDED] Cannot complete {{OPERATION_TYPE}}.
Missing: {{list of missing data points}}
Source suggestion: {{where to find the data}}
Partial output: {{what can be done with available data}}
```
**Behavior:** Output partial results where possible, clearly mark gaps.

### Category 2: Integration Failure
**Trigger:** MCP or API connection fails
**Response pattern:**
```
[INTEGRATION BLOCKED] {{integration_name}} unavailable.
Error: {{error description}}
Retry: Attempting {{retry_count}}/2...
Fallback: Manual execution steps below.
```
**Behavior:**
1. Retry 2x with 5-second delay
2. If still failing: output manual steps to achieve the same result
3. Never silently skip integration-dependent output

### Category 3: Token Budget Exceeded
**Trigger:** Output would exceed token limits for urgency level
**Response pattern:**
```
[OUTPUT CHUNKED] Full report exceeds budget for {{URGENCY}} level.
Delivering: Section 1 of {{total_sections}}
[CONTINUED in next execution]
Summary: {{one-line summary of remaining sections}}
```
**Behavior:** Prioritize highest-impact content first. Offer to continue in next execution.

### Category 4: Ambiguous Request
**Trigger:** Cannot determine operation type or target
**Response pattern:**
```
[CLARIFICATION NEEDED] I detected {{count}} possible interpretations:
1. {{interpretation_1}} → Would trigger: {{command_1}}
2. {{interpretation_2}} → Would trigger: {{command_2}}
Which did you mean? (Or provide more context.)
```
**Behavior:** Never guess. Present top 2 interpretations. Default to the safer option if user says "just do it."

### Category 5: Invalid Output
**Trigger:** Generated output fails validation
**Validation rules:**
- JSON outputs must be valid JSON (parseable)
- Markdown outputs must have required sections (SITUATION, ACTION, RESULT, NEXT)
- Scores must be within valid ranges (0-100)
- Dates must be valid and not in the past (for scheduled actions)
- Currency must use EUR symbol and proper formatting

**Response pattern:**
```
[VALIDATION ERROR] Output failed check: {{check_name}}
Auto-correcting: {{what was fixed}}
```
**Behavior:** Auto-correct where possible. If not auto-correctable, flag for review.

### Category 6: Escalation Required
**Trigger:** Situation exceeds AI capability or authority
**Response pattern:**
```
[ESCALATION NEEDED]
Situation: {{summary}}
Why escalation: {{reason AI cannot resolve}}
Recommended action: {{what a human should do}}
Urgency: {{timeframe}}
```
**Escalation criteria:**
- Financial decisions above €5,000
- Legal/contract interpretation
- Client relationship crisis (potential contract termination)
- Candidate safety or wellbeing concerns
- Data breach or security incident
- Anything requiring wet signature or formal authority

## Retry Logic

```
MAX_RETRIES = 2
RETRY_DELAY = 5 seconds
BACKOFF_MULTIPLIER = 2

attempt = 0
while attempt < MAX_RETRIES:
    result = execute(operation)
    if result.success:
        return result
    attempt += 1
    wait(RETRY_DELAY * (BACKOFF_MULTIPLIER ** attempt))

# All retries exhausted
return fallback_manual_instructions(operation)
```

## Logging Format
Every error produces a log entry:
```json
{
  "timestamp": "ISO-8601",
  "error_category": "missing_data|integration|token|ambiguous|validation|escalation",
  "operation": "{{OPERATION_TYPE}}",
  "severity": "info|warning|error|critical",
  "message": "Human-readable description",
  "resolution": "auto_resolved|manual_fallback|escalated|pending",
  "context": {}
}
```
