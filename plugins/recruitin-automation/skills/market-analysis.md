# Skill: Market Analysis

## Purpose
Provide recruitment market intelligence to inform strategy, pricing, and candidate/client communication.

## Activation
Auto-activated when `{{OPERATION_TYPE}}` is: `lead_scoring`, `content_creation`, `strategic_planning`, `crisis_management`

## Analysis Dimensions

### 1. Demand-Supply Assessment
For a given role/sector:
- **Demand indicators:** job posting volume, client urgency levels, repeat requests
- **Supply indicators:** candidate availability, time-to-fill, application rates
- **Market temperature:** hot (demand >> supply), balanced, cold (supply >> demand)
- **Trend direction:** heating, stable, cooling

### 2. Compensation Benchmarking
When salary data is needed:
- Use available market data + recruitment experience
- Always present as ranges, not fixed numbers
- Flag when client expectations vs market reality diverge
- Include: base salary, bonus potential, benefits, equity (where relevant)
- Segment by: experience level, location (Randstad vs rest of NL), company size

### 3. Sector Pulse
Key recruitment sectors to track:
- **Tech:** software engineering, data, DevOps, product
- **Finance:** accounting, controlling, financial analysis
- **Commercial:** sales, marketing, business development
- **Operations:** supply chain, logistics, project management
- **Healthcare:** medical, pharma, health tech (if applicable)

For each sector:
- Current hiring trend (growing/stable/contracting)
- Hardest roles to fill
- Emerging roles
- Salary movement direction

### 4. Competitive Intelligence
- What are competitor recruitment agencies doing?
- New market entrants or exits
- Pricing pressure (fee % trends)
- Differentiator opportunities

## Confidence Levels
All market analysis outputs MUST include confidence level:
- **HIGH:** Based on direct experience + multiple data points
- **MEDIUM:** Based on indirect signals + limited data
- **LOW:** Based on general knowledge + assumptions
- **[DATA NEEDED]:** Insufficient information to assess

## Usage in Other Skills
- Lead scoring: `market_demand_score` factor
- Content creation: market insights for thought leadership
- Deal rescue: competitive positioning data
- Pipeline report: seasonal and cyclical adjustments

## Output Standards
- Never present estimates as facts
- Always include data freshness: "Based on [period] data"
- Provide ranges, not point estimates
- Flag regional differences (Netherlands is not homogeneous)
- Note when data is Netherlands-specific vs broader EU market
