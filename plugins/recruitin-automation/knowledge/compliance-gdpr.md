# GDPR & Compliance Reference for RecruitIn

## Core Principles

### Data Processing in Recruitment
- **Lawful basis:** Legitimate interest (recruitment is the purpose) OR explicit consent
- **Data minimization:** Only collect what's needed for the specific role
- **Purpose limitation:** Candidate data only used for stated recruitment purpose
- **Storage limitation:** Delete/anonymize data when no longer needed
- **Accuracy:** Keep data current, correct inaccuracies promptly

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
- Explicit consent verification before any outreach template generation

### Audit Ready
- Full decision rationale for every recommendation
- Timestamp on all outputs
- Data lineage (where each input came from)
- Processing activity log format
- Ready for supervisory authority review

## Rules for AI-Generated Content

### NEVER include in outputs:
- Full names paired with salary information
- BSN (Dutch social security numbers)
- Health information or disability status
- Criminal records or background check details
- Age, ethnicity, religion, sexual orientation
- Home addresses or personal phone numbers (without consent context)

### ALLOWED in outputs:
- Anonymized candidate profiles ("Candidate A, 8 years experience in...")
- Aggregated data ("3 candidates at salary range €60-70K")
- Job-related qualifications and experience summaries
- Professional contact information (business email, LinkedIn URL)
- Interview feedback (professional assessment, not personal judgments)

## Dutch Specifics
- **AVG (Algemene Verordening Gegevensbescherming):** Dutch implementation of GDPR
- **Autoriteit Persoonsgegevens:** Dutch supervisory authority
- **Wet allocatie arbeidskrachten door intermediairs (Waadi):** Regulation for intermediaries
- **NEN 4400-1:** Standard for labor intermediary reliability

## Template Compliance Checklist
Before sending any client/candidate communication:
- [ ] No unnecessary PII included
- [ ] Data source is legitimate and documented
- [ ] Recipient has right to receive this information
- [ ] Unsubscribe/opt-out mechanism available (for marketing)
- [ ] Content does not discriminate (Wet gelijke behandeling)
- [ ] Job requirements are genuine and non-discriminatory
