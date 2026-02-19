# Hook: Session Start

## Purpose
Automatically initialize RecruitIn context when a Claude Code session starts.

## Trigger
Session start event (when user opens Claude Code in this project)

## Behavior
On session start:
1. Read `plugins/recruitin-automation/workflows/current-state.md` for last known pipeline state
2. Check if pipeline data is stale (>24h since last update)
3. If stale: suggest running `/daily-ops`
4. Display available commands summary

## Welcome Message
```
RecruitIn AI geladen. Laatste pipeline update: [timestamp from current-state.md]

Beschikbare commando's:
  /daily-ops          — Dagelijks overzicht
  /deal-rescue        — Deals redden
  /lead-score         — Leads scoren
  /content-create     — Content maken
  /pipeline-report    — Pipeline analyse
  /integration-check  — Integraties checken
  /strategic-planning — Strategische planning
  /crisis             — Crisis response

Type een commando of beschrijf wat je nodig hebt.
```

## Stale Data Warning
If last update >24h:
```
[STALE DATA] Pipeline data is [X] uur oud. Run /daily-ops voor een update.
```

## MCP Status Check
If `.mcp.json` configured but env vars missing:
```
[SETUP NEEDED] MCP integraties geconfigureerd maar API keys ontbreken.
Stel in: export PIPEDRIVE_API_TOKEN='...'
Zie: .mcp.json voor alle vereiste variabelen.
```
