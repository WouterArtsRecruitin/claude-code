# Automation Chains — RecruitIn Workflows

## Overview
Automation chains define sequences of commands and skills that execute together. Each chain has a trigger, execution order, and expected output.

---

## Chain 1: Morning Routine
**Trigger:** Manual (`/daily-ops`) or scheduled (daily 08:00)
**Purpose:** Complete daily operations briefing

```
Step 1: Load current-state.md
Step 2: Execute pipeline-management skill → get pipeline snapshot
Step 3: Execute lead-scoring skill → score new leads from last 24h
Step 4: Execute communication-templates skill → generate follow-up queue
Step 5: Compile daily-ops output
Step 6: Update current-state.md
Step 7: Output report to user
```

**Error handling:** If any step fails, continue with remaining steps and flag failures in report.

---

## Chain 2: Deal Rescue Protocol
**Trigger:** Manual (`/deal-rescue`) or auto (deal stalled > SLA)
**Purpose:** Recover at-risk deals

```
Step 1: Load current-state.md
Step 2: Execute pipeline-management skill → identify at-risk deals
Step 3: Execute deal-recovery skill → diagnose each deal
Step 4: Execute communication-templates skill → generate recovery messages
Step 5: Compile deal-rescue output
Step 6: Present for approval (NOT auto-execute)
Step 7: On approval → update current-state.md with actions taken
```

**Error handling:** If deal data insufficient, request manual input before proceeding.

---

## Chain 3: Content Sprint
**Trigger:** Manual (`/content-create`)
**Purpose:** Batch content creation

```
Step 1: Determine content type and channel
Step 2: Execute market-analysis skill → current market context
Step 3: Execute communication-templates skill → base templates
Step 4: Content strategist agent → generate drafts + variants
Step 5: Compliance check (GDPR, inclusive language)
Step 6: Present drafts for review
Step 7: On approval → output final versions with metadata
```

---

## Chain 4: Weekly Pipeline Review
**Trigger:** Manual (`/pipeline-report weekly`) or scheduled (Friday 16:00)
**Purpose:** Weekly business intelligence

```
Step 1: Load current-state.md
Step 2: Execute pipeline-management skill → full analysis
Step 3: Execute market-analysis skill → market context overlay
Step 4: Pipeline analyst agent → forecasting + trend analysis
Step 5: Execute lead-scoring skill → re-score existing pipeline
Step 6: Identify deals needing rescue → flag for Chain 2
Step 7: Compile weekly report
Step 8: Update current-state.md
```

---

## Chain 5: Integration Health
**Trigger:** Manual (`/integration-check`) or auto (error detected)
**Purpose:** Ensure tool integrations are working

```
Step 1: Check each integration endpoint status
Step 2: Verify last sync timestamps
Step 3: Review error logs (24h window)
Step 4: Test data flow integrity
Step 5: Generate health report
Step 6: If issues found → output fix instructions
Step 7: If critical → flag for immediate attention
```

---

## Chain 6: Crisis Response
**Trigger:** Manual (urgent situation detected)
**Purpose:** Rapid response to hiring freezes, competitor threats, key loss

```
Step 1: Assess situation severity (market-analysis skill)
Step 2: Full pipeline impact analysis (pipeline-management skill)
Step 3: Identify at-risk deals (deal-recovery skill)
Step 4: Generate communication plan (communication-templates skill)
Step 5: Scenario planning: best/expected/worst outcomes
Step 6: Present action plan for immediate approval
Step 7: Execute approved actions
Step 8: Set monitoring schedule
```

**Approval:** ALWAYS requires explicit approval. No auto-execution.

---

## Chain Dependencies

```
Morning Routine ──→ Deal Rescue (if at-risk deals found)
                ──→ Content Sprint (if content gap identified)

Weekly Review ────→ Deal Rescue (flagged deals)
              ────→ Content Sprint (strategy update)
              ────→ Integration Health (if sync issues noted)

Crisis Response ──→ All chains potentially activated
```
