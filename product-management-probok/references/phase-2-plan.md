# Phase 2 — Plan

> "How will we build it, and when?"

The Plan phase translates vision into actionable roadmaps, requirements, and risk mitigation strategies.

## Deliverable 1: Product Requirements Document (PRD)

### Purpose
The single source of truth for what the product must do, organized by feature area.

### Required Sections
1. **Document Purpose & Scope** — What this PRD covers
2. **Product Overview** — Brief product description and target users
3. **Feature Requirements by Phase** — Grouped by release/milestone
   - Feature name, description, priority (P0-P3), status (shipped/planned/deferred)
   - User stories in "As a [user], I want [action], so that [benefit]" format
4. **Data Model** — Key entities and relationships
5. **API Requirements** — External services and integration points
6. **Non-Functional Requirements** — Performance, accessibility, security, localization
7. **Out of Scope** — Explicitly excluded features
8. **Dependencies** — External dependencies and assumptions

### How to Populate
- Read existing PRD if one exists; update rather than replace
- Scan all View/ViewModel files for feature inventory
- Check model files for data entities
- Review service layer for API integrations
- Map TODO/FIXME comments to deferred requirements

---

## Deliverable 2: Product Roadmap

### Purpose
Timeline visualization of what ships when, with dependencies and milestones.

### Required Sections
1. **Roadmap Overview** — High-level timeline (quarters or months)
2. **Phase Breakdown** — Per-phase goals, features, and target dates
3. **Milestone Definitions** — Clear criteria for each milestone
4. **Sprint Plans** — Near-term sprint-level detail (2-4 sprints ahead)
5. **Dependency Graph** — What blocks what
6. **Decision Points** — Key decisions that affect the roadmap
7. **Buffer Allocation** — Built-in time for unknowns
8. **Roadmap Risks** — Threats to the timeline

### How to Populate
- Extract from existing PM_TODO, backlog, or project board
- Analyze git tags/releases for historical velocity
- Check for feature flags indicating planned features
- Map TODO comments to future work items

---

## Deliverable 3: Resource and Capacity Plan

### Purpose
Define who does what, with what capacity, and identify resource gaps.

### Required Sections
1. **Team Structure** — Current team composition and roles
2. **Capacity Allocation** — Hours/percentage per phase or workstream
3. **Skill Matrix** — Skills available vs. skills needed
4. **Tool Stack** — Development, design, project management tools
5. **AI/Automation Leverage** — How AI tools augment capacity
6. **Velocity Metrics** — Historical delivery rate
7. **Scaling Plan** — When and how to add resources
8. **Constraints** — Budget, time, or capability limitations

### How to Populate
- Check git log for contributor count and commit frequency
- Identify tools from config files (Xcode, VS Code, CI/CD)
- Calculate velocity from release cadence in CHANGELOG
- Note AI tool usage from CLAUDE.md or similar configs

---

## Deliverable 4: Risk Assessment and Mitigation

### Purpose
Identify, categorize, and plan mitigations for all project risks.

### Required Sections
1. **Risk Register** — Table with ID, category, description, probability, impact, score
2. **Risk Categories** — Technical, Business, Operational, External
3. **Heat Map** — Probability vs. Impact visualization
4. **Mitigation Strategies** — Per-risk action plans
5. **Assumptions Log** — Assumptions that if wrong, become risks
6. **Issues Log** — Risks that have materialized
7. **Dependencies Log** — External dependencies and their risk profiles
8. **Review Cadence** — How often to reassess risks

### How to Populate
- Scan for error handling patterns to identify known failure modes
- Check API dependencies for single-point-of-failure risks
- Review platform version requirements for compatibility risks
- Look for hardcoded values, missing error handling, or TODO markers

---

## Deliverable 5: Success Metrics and KPIs

### Purpose
Define how success is measured at every level — product, feature, and operational.

### Required Sections
1. **North Star Metric** — The one metric that matters most
2. **OKRs by Phase** — Objectives and Key Results per milestone
3. **Core Funnel Metrics** — Acquisition, activation, retention, revenue, referral
4. **Feature-Level KPIs** — Per-feature success criteria
5. **Operational Metrics** — Crash rate, API latency, error rates
6. **Measurement Plan** — What events to track, with event schema
7. **Reporting Cadence** — Daily/weekly/monthly reporting schedule
8. **Experiment Roadmap** — Planned A/B tests and hypotheses

### How to Populate
- Check for analytics SDK integration (Firebase, Mixpanel, TelemetryDeck, etc.)
- Scan for event tracking calls in the codebase
- Read existing METRICS or KPI docs
- Infer funnel from navigation flow (onboarding → core action → retention)

---

## Deliverable 6: Stakeholder Communication Plan

### Purpose
Define who needs to know what, when, and through which channels.

### Required Sections
1. **Stakeholder Map** — Internal and external stakeholders with influence/interest
2. **Communication Matrix** — Who gets what update, how often, via what channel
3. **Update Templates** — Standard formats for status updates
4. **Feedback Collection** — How stakeholder input is gathered and processed
5. **Escalation Paths** — When and how to escalate issues
6. **Decision Authority** — Who approves what (RACI matrix)
7. **External Communications** — Press, users, partners
8. **Review Schedule** — Cadence for stakeholder check-ins

### How to Populate
- Identify stakeholders from README (contributors, sponsors, users)
- Check for TestFlight/beta configuration indicating beta testers
- Look for social media links or community channels
- Review any existing communication templates in docs/
