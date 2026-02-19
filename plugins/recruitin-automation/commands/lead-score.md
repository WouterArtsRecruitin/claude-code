# /lead-score — Lead Scoring Command

Score and prioritize leads based on recruitment-specific criteria.

## Trigger
`/lead-score` or `/lead-score [lead_data]`

## Variables (auto-set)
```
{{OPERATION_TYPE}} = "lead_scoring"
{{URGENCY}} = "this_week"
{{OUTPUT_AUDIENCE}} = "internal"
{{INTEGRATION_TARGET}} = "pipedrive"
```

## Scoring Model

### Client Lead Scoring (companies looking to hire)
| Factor | Weight | Scoring |
|--------|--------|---------|
| Company size | 20% | Enterprise(10) > Mid(7) > SMB(4) > Startup(2) |
| Hiring urgency | 25% | Immediate(10) > This month(7) > This quarter(4) > Exploring(1) |
| Budget clarity | 15% | Confirmed(10) > Estimated(6) > Unknown(3) > "No budget"(0) |
| Role difficulty | 15% | Niche/Senior(10) > Mid(6) > Junior/Volume(3) |
| Relationship warmth | 15% | Existing client(10) > Referral(8) > Warm intro(5) > Cold(2) |
| Market demand | 10% | High demand role(10) > Medium(6) > Low(3) |

### Candidate Lead Scoring
| Factor | Weight | Scoring |
|--------|--------|---------|
| Availability | 25% | Immediately(10) > 1 month(7) > 3 months(4) > Passive(2) |
| Skill match | 25% | Exact match(10) > Strong(7) > Partial(4) > Weak(1) |
| Salary alignment | 20% | Within range(10) > Negotiable(6) > Above range(3) > Way above(0) |
| Interview readiness | 15% | Ready now(10) > Needs prep(6) > Needs convincing(3) |
| Cultural fit signals | 15% | Strong indicators(10) > Neutral(5) > Red flags(1) |

### Score Interpretation
| Score Range | Priority | Action |
|------------|----------|--------|
| 80-100 | HOT | Immediate personal contact, fast-track pipeline |
| 60-79 | WARM | Schedule within 48h, standard pipeline |
| 40-59 | NURTURE | Add to drip sequence, monthly check-in |
| 20-39 | COLD | Low priority, quarterly review |
| 0-19 | ARCHIVE | No action, archive with re-evaluation trigger |

## Output Format
```markdown
## Lead Score Report — [DATE]

### Scored Leads (highest first)

| Lead | Type | Score | Priority | Recommended Action | Deadline |
|------|------|-------|----------|-------------------|----------|
| [Name/Company] | Client/Candidate | [XX]/100 | HOT/WARM/etc | [Action] | [Date] |

### Score Breakdown (top 5 leads)

#### [Lead Name] — Score: [XX]/100 — [PRIORITY]
| Factor | Score | Notes |
|--------|-------|-------|
| [Factor] | [X]/10 | [Why] |
| ... | ... | ... |

**Recommended next step:** [Specific action]
```
