# RecruitIn Pipeline Stage Reference

## Stage Definitions

### Stage 1: Qualification
- **Goal:** Determine if the lead is worth pursuing
- **Entry criteria:** New lead received (inbound or outbound)
- **Activities:** Initial contact, needs assessment, feasibility check
- **Exit criteria:** Lead qualified (budget, authority, need, timeline confirmed)
- **SLA:** 5 business days
- **Probability:** 10%
- **Common reasons for loss:** Bad fit, no budget, no urgency

### Stage 2: Engagement
- **Goal:** Build relationship and understand detailed requirements
- **Entry criteria:** Lead qualified, mutual interest confirmed
- **Activities:** Discovery calls, job briefings, candidate search initiation
- **Exit criteria:** Full brief received, candidates identified, process agreed
- **SLA:** 10 business days
- **Probability:** 25%
- **Common reasons for loss:** Ghosting, internal hire, competitor preferred

### Stage 3: Proposal / Interview
- **Goal:** Present candidates and manage interview process
- **Entry criteria:** Shortlist ready, client ready to interview
- **Activities:** CV submission, interview scheduling, feedback loops
- **Exit criteria:** Preferred candidate identified, moving to offer
- **SLA:** 14 business days
- **Probability:** 50%
- **Common reasons for loss:** No suitable candidate, process too slow, candidate withdrew

### Stage 4: Negotiation
- **Goal:** Align on terms and secure commitment
- **Entry criteria:** Preferred candidate selected
- **Activities:** Salary negotiation, contract terms, start date discussion
- **Exit criteria:** Verbal offer accepted
- **SLA:** 7 business days
- **Probability:** 75%
- **Common reasons for loss:** Counter-offer accepted, salary gap, candidate cold feet

### Stage 5: Closing
- **Goal:** Finalize placement
- **Entry criteria:** Verbal acceptance received
- **Activities:** Contract signing, reference checks, onboarding prep
- **Exit criteria:** Contract signed, start date confirmed, invoice sent
- **SLA:** 5 business days
- **Probability:** 90%
- **Common reasons for loss:** Contract issues, last-minute withdrawal, background check fail

## Pipedrive Field Mapping

| RecruitIn Field | Pipedrive Field | Type |
|----------------|-----------------|------|
| Deal name | deal.title | text |
| Company | deal.org_name | org |
| Contact | deal.person_name | person |
| Role title | deal.custom_role | text |
| Deal value | deal.value | currency (EUR) |
| Stage | deal.stage_id | stage |
| Lead score | deal.custom_lead_score | number |
| Last activity | deal.last_activity_date | date |
| Expected close | deal.expected_close_date | date |
| Risk level | deal.custom_risk_level | enum |
| Source | deal.custom_source | enum |

## Revenue Model
- **Fee structure:** % of annual salary (standard recruitment)
- **Typical fee:** 20-25% depending on relationship and exclusivity
- **Payment terms:** 50% on start, 50% after guarantee period (typical)
- **Guarantee period:** 3 months (standard), 6 months (executive)
