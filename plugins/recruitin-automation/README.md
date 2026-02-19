# RecruitIn Automation Plugin

> Universal recruitment automation system for RecruitIn — built for Claude Code.

## What This Does

This plugin turns Claude Code into a recruitment operations assistant with:
- **6 slash commands** for daily operations, deal rescue, lead scoring, content creation, pipeline reporting, and integration health checks
- **3 specialized agents** (orchestrator, pipeline analyst, content strategist)
- **5 skills** (lead scoring, pipeline management, communication templates, deal recovery, market analysis)
- **Universal meta-prompt** with variable substitution for consistent, token-efficient execution
- **GDPR-compliant** output handling with three compliance levels

## Quick Start

### 1. Load the Setup Prompt
Add `templates/claude-code-setup.md` as a project knowledge file, or paste its contents at session start.

### 2. Use Commands
```
/daily-ops              → Morning briefing
/deal-rescue            → Recover stalled deals
/lead-score             → Score leads
/content-create linkedin → LinkedIn post draft
/pipeline-report weekly  → Weekly pipeline analysis
/integration-check      → Check tool integrations
```

### 3. Or Just Talk
The orchestrator auto-detects intent:
- "Goedemorgen" → runs daily ops
- "How's the pipeline?" → runs pipeline report
- "This deal is stuck" → runs deal rescue
- "Write a post about hiring trends" → runs content create

## File Structure

```
plugins/recruitin-automation/
├── .claude-plugin/
│   └── plugin.json              # Plugin metadata and registration
├── commands/
│   ├── daily-ops.md             # /daily-ops command definition
│   ├── deal-rescue.md           # /deal-rescue command definition
│   ├── lead-score.md            # /lead-score command definition
│   ├── content-create.md        # /content-create command definition
│   ├── pipeline-report.md       # /pipeline-report command definition
│   └── integration-check.md     # /integration-check command definition
├── agents/
│   ├── recruitment-orchestrator.md  # Central routing agent
│   ├── pipeline-analyst.md          # Pipeline analysis specialist
│   └── content-strategist.md        # Content creation specialist
├── skills/
│   ├── lead-scoring.md          # Lead scoring models (CLS + CALS)
│   ├── pipeline-management.md   # Pipeline stages, metrics, thresholds
│   ├── communication-templates.md # Email/message templates (NL/EN)
│   ├── deal-recovery.md         # 5 recovery playbooks
│   └── market-analysis.md       # Market intelligence framework
├── knowledge/
│   ├── recruitin-commands-library.md  # Command reference (read-only)
│   ├── pipeline-stages.md             # Stage definitions (read-only)
│   └── compliance-gdpr.md            # GDPR reference (read-only)
├── workflows/
│   ├── current-state.md         # Live pipeline state (actively updated)
│   └── automation-chains.md     # Workflow definitions
├── templates/
│   ├── meta-prompt.md           # Universal meta-prompt with {{VARIABLES}}
│   ├── claude-code-setup.md     # Claude Code initialization prompt
│   └── error-handling.md        # Error handling strategy
└── README.md                    # This file
```

## Architecture Decisions

| Decision | Choice | Rationale |
|----------|--------|-----------|
| Output format | Markdown + JSON | MD for humans, JSON for APIs |
| Language | Dutch primary | Netherlands market, English on request |
| State management | Git-tracked MD files | Version history = audit trail |
| Token strategy | Reference files, never inline | Minimize per-execution cost |
| Approval flow | Auto for reports, draft for actions | Safety without friction |
| Compliance | Three-tier GDPR levels | Standard daily use + strict when needed |

## Variables Reference

### Primary (required)
| Variable | Values | Purpose |
|----------|--------|---------|
| `{{OPERATION_TYPE}}` | daily_routine, deal_rescue, lead_scoring, content_creation, pipeline_report, integration_check, strategic_planning, crisis_management | Determines skill activation |
| `{{URGENCY}}` | asap, this_week, this_month, strategic | Controls depth and word limits |
| `{{PIPELINE_STATE}}` | "X deals \| €Y total \| Stage: [...]" | Pipeline context |
| `{{OUTPUT_AUDIENCE}}` | internal, client, public, system | Format and tone selection |

### Secondary (optional)
| Variable | Values | Purpose |
|----------|--------|---------|
| `{{INTEGRATION_TARGET}}` | pipedrive, zapier, email, slack, jotform, linkedin | Output structure additions |
| `{{BUDGET_CONTEXT}}` | Euro amount or "flexible" | Financial constraint |
| `{{RISK_LEVEL}}` | low, medium, high, critical | Priority flagging |
| `{{COMPLIANCE_LEVEL}}` | standard, gdpr_strict, audit_ready | Data handling strictness |
| `{{MARKET_CONDITION}}` | stable, boom, crisis, unknown | Strategy adjustment |

## Version History
- **v1.0.0** — Initial release. 6 commands, 3 agents, 5 skills, full knowledge base.
