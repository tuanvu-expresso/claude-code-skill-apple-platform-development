# Phase 1 — Conceive

> "Why should this product exist?"

The Conceive phase establishes the strategic foundation. Every document answers why the product deserves investment before any planning or development begins.

## Deliverable 1: Product Vision Statement

### Purpose
Define the north star — what the product aspires to become and why it matters.

### Required Sections
1. **Mission Statement** — One sentence: what the product does for whom
2. **Vision Statement** — One sentence: aspirational future state (2-3 year horizon)
3. **Elevator Pitch** — 30-second explanation for stakeholders
4. **Product Principles** — 4-6 guiding principles ranked by priority
5. **Problem Statement** — The specific pain point being addressed
6. **Target Audience** — Primary and secondary user segments
7. **Long-Term Vision** — Phase progression from MVP to mature product
8. **Success Definition** — What "winning" looks like at each milestone

### How to Populate
- Extract from README, CLAUDE.md, or any existing vision docs
- Infer from feature set and user flows in the codebase
- If no vision exists, analyze the app's core value proposition from its features

---

## Deliverable 2: Market Opportunity Analysis

### Purpose
Quantify the market size and validate that the opportunity is worth pursuing.

### Required Sections
1. **Market Context** — Industry overview and current landscape
2. **Problem-Solution Gap** — What existing solutions miss
3. **Market Sizing** — TAM / SAM / SOM with methodology
4. **Timing Analysis** — Why now? Technology, market, or cultural tailwinds
5. **Growth Trends** — Category growth data and projections
6. **Revenue Opportunity** — Monetization potential by model (freemium, subscription, one-time)
7. **Entry Barriers** — What makes this market hard to enter
8. **Risk Factors** — Market-level risks (saturation, regulation, platform dependency)

### How to Populate
- Use WebSearch for market data (app category size, growth rates)
- Analyze App Store / Play Store category rankings
- Identify the app's category from its Info.plist or manifest
- Check for monetization code (StoreKit, billing, ads) to infer revenue model

---

## Deliverable 3: Competitive Landscape

### Purpose
Map competitors, identify differentiation, and find whitespace opportunities.

### Required Sections
1. **Direct Competitors** — Apps solving the same problem (3-5 minimum)
2. **Indirect Competitors** — Adjacent solutions users might choose instead
3. **Feature Comparison Matrix** — Table comparing key features across competitors
4. **Pricing Analysis** — How competitors monetize
5. **Strengths & Weaknesses** — Per competitor SWOT summary
6. **Positioning Map** — 2x2 matrix plotting competitors on key dimensions
7. **Differentiation Strategy** — What makes this product unique
8. **Competitive Moats** — Sustainable advantages (data, UX, community, technology)

### How to Populate
- WebSearch for top apps in the category
- Analyze App Store reviews of competitors for unmet needs
- Compare feature sets against the project's own feature list
- Check API integrations for unique data source advantages

---

## Deliverable 4: User Personas and Needs

### Purpose
Define who the users are, what they need, and what jobs they hire the product to do.

### Required Sections
1. **Primary Persona** — Detailed profile with demographics, goals, frustrations
2. **Secondary Persona** — Second user type with distinct needs
3. **Jobs to Be Done (JTBD)** — Functional, emotional, and social jobs per persona
4. **Pain Points** — Current pain points with severity ratings
5. **User Journey Map** — Key touchpoints from discovery to daily use
6. **Feature-Persona Mapping** — Which features serve which persona
7. **Behavioral Patterns** — Usage frequency, session length, peak times
8. **Unmet Needs** — What personas want but no solution provides

### How to Populate
- Infer personas from the app's features and UI flows
- Check for analytics events that reveal user behavior patterns
- Review onboarding flows for how the app introduces itself
- Look for user segmentation in the codebase (user types, preferences)

---

## Deliverable 5: Business Case

### Purpose
Financial justification — costs, revenue projections, and ROI calculation.

### Required Sections
1. **Executive Summary** — One-paragraph business case
2. **Cost Structure** — Development, infrastructure, API, marketing costs
3. **Revenue Model** — How the product will generate revenue
4. **Revenue Projections** — 12-month forecast with assumptions
5. **Break-Even Analysis** — When revenue exceeds costs
6. **ROI Calculation** — Expected return on investment
7. **Sensitivity Analysis** — Best/expected/worst case scenarios
8. **Go/No-Go Criteria** — Measurable thresholds for proceeding

### How to Populate
- Scan for API keys and service integrations to estimate infrastructure costs
- Check Podfile/Package.swift for paid SDK dependencies
- Look for StoreKit/billing code to understand revenue model
- Estimate development cost from commit history and team size

---

## Deliverable 6: Concept Validation Summary

### Purpose
Document what was validated, what pivoted, and lessons from the conceive phase.

### Required Sections
1. **Technical Feasibility** — Can we build this? Key technical risks tested
2. **Data Source Validation** — API/data provider evaluation and selection
3. **UX Validation** — User interface assumptions tested
4. **Architecture Decisions** — Key architectural choices and rationale
5. **Pivot History** — What changed from initial concept and why
6. **Prototype Results** — What was built to validate assumptions
7. **Open Questions** — Remaining unknowns carried into Plan phase
8. **Recommendation** — Proceed, pivot, or kill assessment

### How to Populate
- Check git history for major pivots (API changes, architecture refactors)
- Look for deprecated code or TODO comments indicating abandoned approaches
- Read CHANGELOG for evolution of the product concept
- Identify any A/B test infrastructure or experiment code
