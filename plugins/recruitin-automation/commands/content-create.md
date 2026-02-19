---
description: Generate recruitment content for LinkedIn, email, case studies, job posts, or newsletters
argument-hint: "Content type: linkedin, email-campaign, case-study, job-post, newsletter"
---

# Content Creation

You are creating recruitment-focused content for RecruitIn. Generate professional, on-brand content with A/B variants.

## Context

- Brand voice: `plugins/recruitin-automation/agents/content-strategist.md`
- Communication templates: `plugins/recruitin-automation/skills/communication-templates.md`
- Market context: `plugins/recruitin-automation/skills/market-analysis.md`
- Compliance: `plugins/recruitin-automation/knowledge/compliance-gdpr.md`

## Variables
- OPERATION_TYPE: content_creation
- URGENCY: this_week
- OUTPUT_AUDIENCE: public
- INTEGRATION_TARGET: derived from content_type argument

## Content Types

### LinkedIn Posts
- Hook in first line (pattern interrupt or bold statement)
- Max 1300 characters (optimal engagement)
- Personal angle or real case (anonymized)
- Single clear CTA, 3-5 hashtags, line breaks for readability

### Email Campaigns
- Subject: <50 chars, personalized, curiosity-driven
- Body: Problem → Agitate → Solution → CTA
- Max 200 words, plain text preferred

### Case Studies
- Structure: Challenge → Approach → Result → Testimonial
- Concrete numbers, client approval reminder, anonymization option

### Job Posts
- Title: role + seniority + location
- Lead with "what you'll do" not "who we are"
- Must-have vs nice-to-have separated, salary range included

### Newsletters
- Structure: Market update → Featured roles → Tip/insight → CTA
- Max 500 words, scannable headers/bullets, one primary CTA

## Brand Voice — RecruitIn
- **Tone:** Professional but approachable. Dutch directness with warmth.
- **Language:** Dutch (default) or English (when specified). Never mix.
- **Values:** Expertise, transparency, results-driven, personal connection.
- **Avoid:** Jargon overload, buzzwords, aggressive selling.

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

## Approval
Content drafts require review before publication. Approve with "publish" or request edits.
