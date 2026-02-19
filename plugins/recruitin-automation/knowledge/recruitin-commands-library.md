# RecruitIn Commands Library v1.1.0

## Quick Reference

| Command | Purpose | Urgency | Auto-Execute |
|---------|---------|---------|--------------|
| `/daily-ops` | Morning operations check | this_week | Yes |
| `/deal-rescue` | Recover stalled deals | asap | Draft first |
| `/lead-score` | Score and prioritize leads | this_week | Yes |
| `/content-create` | Generate content | this_week | Draft first |
| `/pipeline-report` | Pipeline analysis | this_week | Yes |
| `/integration-check` | Integration health | asap | Yes |
| `/strategic-planning` | Quarterly strategy | strategic | Draft first |
| `/crisis` | Emergency response | asap | Approval required |

## Command Details

### /daily-ops [focus_area]
**What it does:** Generates your morning briefing — pipeline status, priority actions, follow-ups, daily metrics.
**Optional focus:** `candidates`, `clients`, `deals`, `metrics`
**Output:** Internal markdown report
**Skills activated:** lead_scoring, pipeline_management, communication_templates

### /deal-rescue [deal_name_or_id]
**What it does:** Analyzes at-risk deals and generates recovery strategies with ready-to-send messages.
**Optional target:** Specific deal name or Pipedrive ID. Without target: analyzes all at-risk deals.
**Output:** Internal report with recovery playbooks
**Skills activated:** deal_recovery, pipeline_management, communication_templates

### /lead-score [lead_data]
**What it does:** Scores leads using the RecruitIn scoring model (client or candidate).
**Input:** Lead information (name, type, available data points)
**Output:** Score table with priority actions
**Skills activated:** lead_scoring, market_analysis

### /content-create [content_type]
**What it does:** Generates recruitment content for specified channel.
**Types:** `linkedin`, `email-campaign`, `case-study`, `job-post`, `newsletter`
**Output:** Content draft with A/B variants and metadata
**Skills activated:** communication_templates, market_analysis

### /pipeline-report [period]
**What it does:** Comprehensive pipeline analysis with forecasting.
**Periods:** `weekly` (default), `monthly`, `quarterly`
**Output:** Internal report with metrics, forecast, and action items
**Skills activated:** pipeline_management, market_analysis, lead_scoring

### /integration-check [integration_name]
**What it does:** Verifies integration health between tools.
**Targets:** `pipedrive`, `zapier`, `jotform`, `email`, `slack`, or all
**Output:** Health status report with fixes
**Skills activated:** pipeline_management

### /strategic-planning [focus_area]
**What it does:** Generates quarterly strategic analysis — market positioning, resource allocation, growth opportunities.
**Optional focus:** `market`, `revenue`, `team`, `clients`, `growth`
**Output:** Internal strategic report requiring review
**Skills activated:** market_analysis, pipeline_management, lead_scoring

### /crisis [situation_description]
**What it does:** Emergency crisis response — impact analysis, action plan, communication drafts.
**Input:** Description of the crisis (hiring freeze, competitor threat, key client loss, market disruption, internal crisis)
**Output:** Crisis response plan with immediate + 7-day actions. ALWAYS requires explicit approval before any action.
**Skills activated:** deal_recovery, pipeline_management, communication_templates, market_analysis

## Command Chaining Examples

```
# Morning routine
/daily-ops → review → /deal-rescue (if at-risk deals found)

# Weekly planning
/pipeline-report weekly → /lead-score (new leads) → /content-create linkedin

# Crisis response
/crisis → /deal-rescue → /pipeline-report

# Strategic review
/pipeline-report quarterly → /strategic-planning → /content-create linkedin

# Content sprint
/content-create linkedin → /content-create email-campaign → /content-create newsletter
```

## Deprecation Policy
- Deprecated commands marked with `[DEPRECATED v1.x.x]`
- Deprecated commands remain functional for 2 versions
- Replacement command always documented
- Currently deprecated: none (v1.1.0)
