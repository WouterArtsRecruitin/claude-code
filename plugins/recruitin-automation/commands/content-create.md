# /content-create — Content Creation Command

Generate recruitment-focused content for various channels.

## Trigger
`/content-create [content_type]` where content_type is:
- `linkedin` — LinkedIn post
- `email-campaign` — Email sequence
- `case-study` — Client case study
- `job-post` — Job advertisement
- `newsletter` — Recruitment newsletter

## Variables (auto-set)
```
{{OPERATION_TYPE}} = "content_creation"
{{URGENCY}} = "this_week"
{{OUTPUT_AUDIENCE}} = "public"
{{INTEGRATION_TARGET}} = [derived from content_type]
```

## Content Guidelines

### Brand Voice — RecruitIn
- **Tone:** Professional but approachable. Dutch directness with warmth.
- **Language:** Dutch (primary) or English (when specified). Never mix.
- **Values:** Expertise, transparency, results-driven, personal connection.
- **Avoid:** Jargon overload, buzzwords without substance, aggressive selling.

### LinkedIn Posts
- Hook in first line (pattern interrupt or bold statement)
- Max 1300 characters (optimal engagement length)
- Personal angle or real case (anonymized)
- Single clear CTA
- 3-5 relevant hashtags
- Line breaks for readability

### Email Campaigns
- Subject line: <50 characters, personalized, curiosity-driven
- Preview text: complements subject, not repeats
- Body: Problem → Agitate → Solution → CTA
- Max 200 words per email
- Plain text preferred (higher deliverability)

### Case Studies
- Structure: Challenge → Approach → Result → Testimonial
- Include concrete numbers (time-to-hire, cost savings, candidate quality)
- Client approval reminder before publication
- Anonymization option for sensitive placements

### Job Posts
- Title: clear role + seniority + location
- Lead with "what you'll do" not "who we are"
- Requirements: must-have vs nice-to-have clearly separated
- Salary range (transparency = more applicants)
- Application process explained

## Output Format
```markdown
## Content Draft — [TYPE] — [DATE]

### [Title/Subject]

[Content body]

### Metadata
- **Platform:** [target]
- **Language:** [NL/EN]
- **Word count:** [X]
- **CTA:** [description]
- **Hashtags:** [if applicable]

### Variations (A/B)
**Version A:** [variant]
**Version B:** [variant]

### Publishing Notes
- [Timing recommendation]
- [Compliance checks needed]
- [Approval required from: X]
```
