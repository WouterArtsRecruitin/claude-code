# GDPR & Compliance Reference for RecruitIn

## Core Principles (Article 5 GDPR / AVG)

### Lawful Bases for Recruitment Data Processing
The GDPR provides six lawful bases. For recruitment, the relevant ones are:
1. **Legitimate interest (Art. 6(1)(f)):** Primary basis for recruitment activities. REQUIRES a documented balancing test (belangenafweging) weighing RecruitIn's interest against the data subject's rights. Must be documented per processing activity.
2. **Consent (Art. 6(1)(a)):** Use for keeping candidate data beyond the active recruitment process (e.g., talent pool). Must be freely given, specific, informed, unambiguous. Problematic in employment context due to power imbalance — use sparingly.
3. **Contractual necessity (Art. 6(1)(b)):** For candidates in active process — processing needed to take steps at their request prior to entering a contract.
4. **Legal obligation (Art. 6(1)(c)):** For mandatory reporting, tax requirements on placed candidates.

### Key Principles
- **Data minimization:** Only collect what's needed for the specific role
- **Purpose limitation:** Candidate data only used for stated recruitment purpose
- **Storage limitation:** Delete/anonymize per retention schedule (see below)
- **Accuracy:** Keep data current, correct inaccuracies promptly

## Data Retention Periods (Dutch AP Guidance)

| Data Category | Retention Period | Legal Basis |
|--------------|-----------------|-------------|
| Active candidate in process | Duration of recruitment + 4 weeks | Legitimate interest |
| Rejected candidate (no consent) | **Maximum 4 weeks** after rejection | Legitimate interest |
| Rejected candidate (with consent) | **Maximum 1 year** after consent | Consent (Art. 6(1)(a)) |
| Placed candidate | Duration of guarantee period + 2 years | Contractual / Legitimate interest |
| Client contact data | Duration of business relationship + 2 years | Legitimate interest |
| Financial records (invoices) | **7 years** (Dutch fiscal law) | Legal obligation |
| `current-state.md` pipeline data | Overwrite on update; git history = 1 year max | Legitimate interest |

**Action:** Set calendar reminders for data cleanup. Audit quarterly.

## DPIA Requirement (Article 35 GDPR)

### When a DPIA is Required
A Data Protection Impact Assessment is **MANDATORY** when:
- Systematic and extensive profiling with significant effects
- Large-scale processing of special categories of data
- Systematic monitoring of publicly accessible areas

### RecruitIn DPIA Requirements
The **lead scoring system (CLS/CALS)** constitutes automated profiling that affects individuals' opportunities. A DPIA must be conducted and documented covering:
1. Description of processing operations and purposes
2. Assessment of necessity and proportionality
3. Assessment of risks to data subjects
4. Measures to address those risks

**Status:** [DPIA REQUIRED — must be completed before lead scoring is used on real candidate data]

## Article 22: Automated Decision-Making

### Rights of Data Subjects
Candidates have the right to:
1. **Not be subject** to solely automated decisions that significantly affect them
2. **Obtain human intervention** in automated scoring decisions
3. **Express their point of view** on automated assessments
4. **Contest** automated decisions

### Implementation for Lead Scoring
- Lead scores are **advisory, not deterministic** — always present as recommendations
- A human recruiter must make the final decision on candidate action
- On request, explain how a candidate's score was calculated
- Document the human review step in the process
- Include in privacy notice: "We use automated tools to help prioritize candidates. You have the right to request human review of any automated assessment."

## Cross-Border Data Transfers

### Claude/Anthropic Processing
Using Claude Code processes data on Anthropic's infrastructure (US-based). This constitutes a cross-border transfer requiring:
1. **Standard Contractual Clauses (SCCs):** Verify Anthropic's DPA includes EU SCCs
2. **Transfer Impact Assessment (TIA):** Document that US processing with SCCs provides adequate protection
3. **Technical measures:** Minimize PII sent to Claude; use anonymized/pseudonymized data where possible

### Action Items
- [ ] Verify Anthropic verwerkersovereenkomst (Data Processing Agreement) is in place
- [ ] Complete Transfer Impact Assessment for Claude processing
- [ ] Minimize candidate PII in prompts — use anonymized references

## Data Processor Agreement (Verwerkersovereenkomst)

### Required Agreements
| Processor | Purpose | Agreement Status |
|-----------|---------|-----------------|
| Anthropic (Claude) | AI-assisted operations | [REQUIRED — verify DPA] |
| Pipedrive | CRM data storage | [CHECK — should be in place] |
| Zapier | Data routing/automation | [CHECK — should be in place] |
| Jotform | Form data collection | [CHECK — should be in place] |

Each agreement must specify: processing purpose, data categories, retention, security measures, sub-processor list, breach notification procedure.

## Data Breach Protocol (Articles 33-34 GDPR)

### If a Data Breach Occurs
1. **T+0:** Discover and contain the breach
2. **T+24h:** Assess: is there a risk to individuals' rights and freedoms?
3. **T+72h MAXIMUM:** Notify Autoriteit Persoonsgegevens if risk exists
   - Use AP notification form at autoriteitpersoonsgegevens.nl
   - Include: nature of breach, categories/numbers affected, consequences, measures taken
4. **Without undue delay:** Notify affected individuals if HIGH risk
   - Clear language, describe breach, likely consequences, measures taken, contact point

### Breach Register
Maintain a register of ALL breaches (even non-reportable ones) including:
- Date, nature, affected data, affected persons
- Assessment of risk level
- Actions taken
- Notification decisions with reasoning

## Compliance Levels in Prompts

### Standard (default)
- No candidate PII in AI-generated outputs
- Anonymize examples and case studies
- No bulk processing of personal data through prompts
- Reasonable care in data handling

### GDPR Strict
- Every candidate reference includes processing justification
- Data source documented for each data point
- Retention period specified for any stored output
- Right to erasure pathway noted
- Explicit consent verification before outreach template generation

### Audit Ready
- Full decision rationale for every recommendation
- Timestamp on all outputs
- Data lineage (where each input came from)
- Processing activity log format
- Ready for Autoriteit Persoonsgegevens review
- DPIA reference included

## Rules for AI-Generated Content

### NEVER include in outputs:
- Full names paired with salary information
- BSN (Burgerservicenummer / Dutch social security numbers)
- Health information or disability status
- Criminal records or background check details
- Age, ethnicity, religion, sexual orientation
- Home addresses or personal phone numbers (without consent)
- Candidate data sourced without lawful basis

### ALLOWED in outputs (with care):
- Anonymized candidate profiles ("Candidate A, 8+ years in...")
- Aggregated data ("3 candidates at salary range EUR 60-70K")
- Job-related qualifications and experience summaries
- Professional contact information ONLY when legitimately obtained
- Interview feedback (professional assessment, not personal judgments)

## Dutch Specifics

| Law/Standard | Purpose | Status |
|-------------|---------|--------|
| AVG (Algemene Verordening Gegevensbescherming) | Dutch GDPR implementation | Active |
| Autoriteit Persoonsgegevens (AP) | Dutch supervisory authority | Report breaches here |
| Waadi (Wet allocatie arbeidskrachten door intermediairs) | Regulation for staffing intermediaries | Compliance required |
| NEN 4400-1 | SNA certification for labor intermediaries | Recommended |
| Wet gelijke behandeling | Equal treatment law — no discrimination | Must comply in job ads |
| Wet werk en zekerheid (Wwz) | Employment law framework | Relevant for placements |
| UAVG (Uitvoeringswet AVG) | Dutch GDPR implementation details | Supplements AVG |

## Template Compliance Checklist
Before sending any client/candidate communication:
- [ ] No unnecessary PII included
- [ ] Lawful basis documented for data used
- [ ] Data source is legitimate
- [ ] Recipient has right to receive this information
- [ ] Unsubscribe/opt-out available (for marketing, Art. 21 GDPR)
- [ ] Content does not discriminate (Wet gelijke behandeling)
- [ ] Job requirements are genuine occupational requirements
- [ ] Retention period for any stored output is specified
- [ ] Cross-border transfer considerations addressed
