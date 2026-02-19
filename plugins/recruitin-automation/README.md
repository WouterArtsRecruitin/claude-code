# RecruitIn Automation Plugin v1.1.0

> Universal recruitment automation system for RecruitIn — built for Claude Code.

## What This Does

This plugin turns Claude Code into a recruitment operations assistant with:
- **8 slash commands** for daily ops, deal rescue, lead scoring, content, pipeline reports, integrations, strategic planning, and crisis response
- **3 specialized agents** with proper frontmatter (orchestrator, pipeline analyst, content strategist)
- **5 skills** (lead scoring, pipeline management, communication templates, deal recovery, market analysis)
- **Universal meta-prompt** with variable substitution for consistent, token-efficient execution
- **MCP integration** config for Pipedrive, Zapier, and Jotform APIs
- **GDPR-compliant** with DPIA requirements, retention periods, cross-border transfer provisions, and Article 22 protections
- **Hooks** for session initialization and deal stage monitoring

## Quick Start

### 1. Set Up Integrations (optional)
```bash
export PIPEDRIVE_API_TOKEN='your-token'
export PIPEDRIVE_DOMAIN='yourcompany.pipedrive.com'
export ZAPIER_WEBHOOK_BASE='https://hooks.zapier.com/hooks/catch/YOUR_ID'
export JOTFORM_API_KEY='your-key'
```
Without these, commands operate in template mode (manual data input).

### 2. Use Commands
```
/daily-ops               → Morning briefing
/deal-rescue             → Recover stalled deals
/lead-score              → Score leads
/content-create linkedin → LinkedIn post draft
/pipeline-report weekly  → Weekly pipeline analysis
/integration-check       → Check tool integrations
/strategic-planning Q2   → Quarterly strategy
/crisis                  → Emergency response
```

### 3. Or Just Talk
The orchestrator auto-detects intent:
- "Goedemorgen" → daily ops
- "How's the pipeline?" → pipeline report
- "This deal is stuck" → deal rescue
- "Write a LinkedIn post" → content create
- "We need a Q2 strategy" → strategic planning
- "Client announced hiring freeze" → crisis response

## File Structure

```
plugins/recruitin-automation/
├── .claude-plugin/
│   └── plugin.json              # Plugin metadata (v1.1.0)
├── .mcp.json                    # Pipedrive/Zapier/Jotform API config
├── commands/
│   ├── daily-ops.md             # Daily operations (with frontmatter)
│   ├── deal-rescue.md           # Deal recovery (with frontmatter)
│   ├── lead-score.md            # Lead scoring (with frontmatter)
│   ├── content-create.md        # Content creation (with frontmatter)
│   ├── pipeline-report.md       # Pipeline analysis (with frontmatter)
│   ├── integration-check.md     # Integration health (with frontmatter)
│   ├── strategic-planning.md    # Strategic planning (NEW v1.1)
│   └── crisis.md                # Crisis response (NEW v1.1)
├── agents/
│   ├── recruitment-orchestrator.md  # Central routing (with frontmatter)
│   ├── pipeline-analyst.md          # Pipeline specialist (with frontmatter)
│   └── content-strategist.md        # Content specialist (with frontmatter)
├── skills/
│   ├── lead-scoring.md          # CLS + CALS scoring models
│   ├── pipeline-management.md   # 5-stage pipeline with SLAs
│   ├── communication-templates.md # Dutch/English templates
│   ├── deal-recovery.md         # 5 recovery playbooks
│   └── market-analysis.md       # Market intelligence
├── knowledge/
│   ├── recruitin-commands-library.md  # Command reference
│   ├── pipeline-stages.md             # Stage definitions + Pipedrive mapping
│   └── compliance-gdpr.md            # GDPR with DPIA, Art.22, retention, cross-border
├── hooks/
│   ├── session-start.md         # Session initialization (NEW v1.1)
│   └── deal-stage-monitor.md    # Deal alerts (NEW v1.1)
├── workflows/
│   ├── current-state.md         # Live pipeline state
│   └── automation-chains.md     # 6 workflow chains
├── templates/
│   ├── meta-prompt.md           # Universal meta-prompt v1.1
│   ├── claude-code-setup.md     # Session initialization prompt
│   └── error-handling.md        # Error handling strategy
└── README.md                    # This file
```

## What Changed in v1.1.0

| Fix | Before | After |
|-----|--------|-------|
| Command frontmatter | Missing (not registrable) | YAML frontmatter on all 8 commands |
| Agent frontmatter | Missing (not instantiable) | name, description, model, color, tools on all 3 agents |
| plugin.json author | Flat string | Object with name + email |
| MCP config | Missing | `.mcp.json` with Pipedrive, Zapier, Jotform |
| Strategic planning | No command, no routing | `/strategic-planning` command + routing |
| Crisis response | No command, no routing | `/crisis` command + routing |
| GDPR compliance | Surface-level | DPIA, Article 22, retention periods, cross-border, breach protocol |
| Hooks | None | session-start + deal-stage-monitor |
| Token budget | Contradictory (500 words for deal rescue) | Urgency controls depth, not completeness |
| Pipeline state format | Rigid | Accepts any format (structured, natural language, JSON, CSV) |
| Conflict resolution | Missing | Multi-operation handling documented |

## Architecture Decisions

| Decision | Choice | Rationale |
|----------|--------|-----------|
| Output format | Markdown + JSON | MD for humans, JSON for APIs |
| Language | Dutch primary | Netherlands market, English on request |
| State management | Git-tracked MD files | Version history = audit trail |
| Token strategy | Reference files, never inline | Minimize per-execution cost |
| Approval flow | Auto for reports, draft for actions | Safety without friction |
| Compliance | Three-tier GDPR (standard/strict/audit) | Standard daily + strict when needed |
| MCP | Config-ready, env-var driven | Works without keys (template mode), full power with keys |
| Lead scoring | Advisory, not deterministic | Article 22 GDPR compliance |

## Variables Reference

### Primary (required)
| Variable | Values | Purpose |
|----------|--------|---------|
| `{{OPERATION_TYPE}}` | daily_routine, deal_rescue, lead_scoring, content_creation, pipeline_report, integration_check, strategic_planning, crisis_management | Skill activation |
| `{{URGENCY}}` | asap, this_week, this_month, strategic | Depth control |
| `{{PIPELINE_STATE}}` | Any format (structured, natural language, JSON, CSV) | Pipeline context |
| `{{OUTPUT_AUDIENCE}}` | internal, client, public, system | Format + tone |

### Secondary (optional)
| Variable | Values | Purpose |
|----------|--------|---------|
| `{{INTEGRATION_TARGET}}` | pipedrive, zapier, email, slack, jotform, linkedin | Output structure |
| `{{BUDGET_CONTEXT}}` | Euro amount or "flexible" | Financial constraint |
| `{{RISK_LEVEL}}` | low, medium, high, critical | Priority flagging |
| `{{COMPLIANCE_LEVEL}}` | standard, gdpr_strict, audit_ready | Data handling |
| `{{MARKET_CONDITION}}` | stable, boom, crisis, unknown | Strategy adjustment |

## Version History
- **v1.1.0** — Structural fixes: frontmatter on all commands/agents, MCP config, `/strategic-planning` + `/crisis` commands, comprehensive GDPR (DPIA, Art.22, retention, cross-border), hooks, token budget fix, conflict resolution.
- **v1.0.0** — Initial release. 6 commands, 3 agents, 5 skills, full knowledge base.
