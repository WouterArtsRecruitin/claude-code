# Claude Code Terminal Integration — Direct Setup Guide

## Purpose
This document defines how to use RecruitIn Automation directly in the Claude Code terminal, without any external setup beyond `claude` CLI.

---

## METHOD 1: CLAUDE.md Integration (Recommended)

Add this to your project's `CLAUDE.md` file to auto-load RecruitIn context in every session:

```markdown
# RecruitIn Recruitment Automation

## System Context
You are operating as RecruitIn AI, a recruitment operations assistant for RecruitIn (Netherlands-based).

## Available Commands
Run these slash commands for recruitment operations:
- /daily-ops — Morning operations briefing
- /deal-rescue — Recover at-risk deals
- /lead-score — Score client and candidate leads
- /content-create — Generate recruitment content
- /pipeline-report — Pipeline analysis and forecasting
- /integration-check — Integration health check
- /strategic-planning — Quarterly strategy
- /crisis — Emergency crisis response

## Knowledge Files
Reference these files for recruitment context (read, never inline):
- plugins/recruitin-automation/knowledge/pipeline-stages.md
- plugins/recruitin-automation/knowledge/compliance-gdpr.md
- plugins/recruitin-automation/skills/*.md

## Rules
- Output in Dutch by default, English when asked
- Follow SITUATION → ACTION → RESULT → NEXT structure
- Never hallucinate deal/candidate/company data
- GDPR compliant: no PII without justification
- Lead scores are advisory — human makes final decisions
```

### How to Set Up
```bash
# Navigate to your project root
cd /path/to/your/project

# Create or append to CLAUDE.md
cat >> CLAUDE.md << 'EOF'
[paste the above content]
EOF

# Claude Code will auto-read CLAUDE.md on session start
claude
```

---

## METHOD 2: Direct Terminal Workflow

### Daily Workflow — Morning Routine
```bash
# Start Claude Code
claude

# In the Claude Code terminal:
> /daily-ops

# Claude reads pipeline state, generates briefing
# If pipeline data is stale:
> Here's today's pipeline: 25 deals, €400K total, S1:6 S2:9 S3:5 S4:3 S5:2

# Follow up with specific actions:
> /deal-rescue TechCorp
> /lead-score "New lead: Acme Corp, enterprise, hiring 3 devs, budget confirmed"
```

### Content Workflow
```bash
> /content-create linkedin
# Claude generates post with A/B variants
# Review and approve:
> Version A looks good, make it shorter
# Claude refines
> publish
```

### Weekly Review
```bash
> /pipeline-report weekly
# Claude generates full analysis
# If issues found:
> /deal-rescue
# Rescue stalled deals
> /strategic-planning
# Plan next quarter
```

### Crisis Mode
```bash
> /crisis Client XYZ just announced a hiring freeze, they represent 30% of our pipeline
# Claude executes crisis protocol: impact analysis, action plan, communication drafts
# Review and approve each action
```

---

## METHOD 3: Shell Aliases for Quick Access

Add to your `~/.bashrc` or `~/.zshrc`:

```bash
# RecruitIn Quick Commands
alias ri='claude'
alias ri-daily='claude -p "/daily-ops"'
alias ri-pipeline='claude -p "/pipeline-report weekly"'
alias ri-rescue='claude -p "/deal-rescue"'
alias ri-score='claude "/lead-score"'
alias ri-content='claude "/content-create"'
alias ri-crisis='claude "/crisis"'
```

> **Security note:** Do NOT store API tokens (PIPEDRIVE_API_TOKEN, etc.) directly in
> shell rc files. Use a secrets manager, `.env` file (excluded from version control),
> or `direnv` with a `.envrc` that is gitignored.

Usage:
```bash
ri-daily          # Quick morning briefing
ri-pipeline       # Weekly pipeline report
ri-rescue         # Check at-risk deals
ri-content        # Start content creation session
```

---

## METHOD 4: Git Hook Integration

### Pre-commit State Update
Create `.git/hooks/pre-commit`:
```bash
#!/bin/bash
# Update pipeline state timestamp on commit
if [ -f "plugins/recruitin-automation/workflows/current-state.md" ]; then
  TIMESTAMP=$(date -u +"%Y-%m-%dT%H:%M:%SZ")
  sed -i "s/\[DATE:.*\]/[DATE: $TIMESTAMP]/" \
    plugins/recruitin-automation/workflows/current-state.md
fi
```

---

## METHOD 5: Scheduled Operations with Cron

### Daily Morning Brief (auto-generate)
```bash
# Create a private output directory (run once)
mkdir -p "$HOME/.recruitin/reports" && chmod 700 "$HOME/.recruitin/reports"

# Add to crontab: crontab -e
# Run daily-ops at 8:00 AM on weekdays
0 8 * * 1-5 cd /path/to/project && claude -p "/daily-ops" > "$HOME/.recruitin/reports/daily-$(date +\%Y\%m\%d).md" 2>&1

# Weekly pipeline report on Fridays at 4 PM
0 16 * * 5 cd /path/to/project && claude -p "/pipeline-report weekly" > "$HOME/.recruitin/reports/weekly-$(date +\%Y\%m\%d).md" 2>&1
```

---

## TERMINAL SESSION ARCHITECTURE

```
┌─────────────────────────────────────────┐
│           Claude Code Terminal           │
│                                         │
│  CLAUDE.md ──→ Auto-loads RecruitIn AI  │
│                                         │
│  ┌───────────────────────────────────┐  │
│  │  User Input                       │  │
│  │  "Goedemorgen" / /daily-ops      │  │
│  └──────────────┬────────────────────┘  │
│                 │                        │
│  ┌──────────────▼────────────────────┐  │
│  │  Recruitment Orchestrator Agent    │  │
│  │  - Detects intent                 │  │
│  │  - Sets {{VARIABLES}}             │  │
│  │  - Routes to command              │  │
│  └──────────────┬────────────────────┘  │
│                 │                        │
│  ┌──────────────▼────────────────────┐  │
│  │  Command Execution                │  │
│  │  - Loads skill references         │  │
│  │  - Reads current-state.md         │  │
│  │  - Queries MCP (if configured)    │  │
│  │  - Generates SITUATION-ACTION-    │  │
│  │    RESULT-NEXT output             │  │
│  └──────────────┬────────────────────┘  │
│                 │                        │
│  ┌──────────────▼────────────────────┐  │
│  │  Output + State Update            │  │
│  │  - Display results to user        │  │
│  │  - Update current-state.md        │  │
│  │  - Trigger hooks (if applicable)  │  │
│  └───────────────────────────────────┘  │
│                                         │
│  Token Budget: ~2000 input / execution  │
│  State: Local file (gitignored for GDPR) │
│  MCP: Optional (template mode fallback) │
└─────────────────────────────────────────┘
```

## ENVIRONMENT VARIABLES

Use a `.env` file (gitignored) or a secrets manager — do NOT hardcode tokens in shell profiles.

```bash
# .env file (add to .gitignore!)
PIPEDRIVE_API_TOKEN='your-pipedrive-api-token'
PIPEDRIVE_DOMAIN='yourcompany.pipedrive.com'
ZAPIER_WEBHOOK_BASE='https://hooks.zapier.com/hooks/catch/YOUR_ID'
JOTFORM_API_KEY='your-jotform-api-key'

# Load with direnv (.envrc) or: set -a; source .env; set +a
```

```bash
# Optional: Claude Code model configuration
export CLAUDE_MODEL='claude-sonnet-4-5-20250929'  # Default model for speed
# Use claude-opus-4-6 for strategic planning and deep analysis
```

## FIRST-TIME SETUP CHECKLIST

```bash
# 1. Install Claude Code
npm install -g @anthropic-ai/claude-code

# 2. Navigate to project
cd /path/to/your/recruitin-project

# 3. Ensure CLAUDE.md exists with RecruitIn context (see Method 1)

# 4. Set environment variables (optional, for MCP)
# Use .env file + direnv, or a secrets manager (see ENVIRONMENT VARIABLES section)

# 5. Start Claude Code
claude

# 6. Verify setup
> /daily-ops
# Should generate a daily operations report (or request pipeline data)

# 7. Initialize pipeline state
> Here's our current pipeline: [paste Pipedrive data]
# Claude updates current-state.md

# Done! System is operational.
```

## TROUBLESHOOTING

| Issue | Cause | Fix |
|-------|-------|-----|
| Commands not recognized | CLAUDE.md not loaded | Check file exists at project root |
| "DATA NEEDED" on every command | No pipeline state | Provide initial pipeline data or connect Pipedrive |
| MCP connection failed | Missing env vars | Set PIPEDRIVE_API_TOKEN etc. |
| Output in wrong language | No language preference set | Specify in CLAUDE.md or per-request |
| Token errors | Context too large | Plugin references files, shouldn't hit limits normally |
