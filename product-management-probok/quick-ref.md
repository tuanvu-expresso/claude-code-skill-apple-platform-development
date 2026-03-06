# ProBOK Quick Reference

Fast lookup for phase selection, document identification, and common workflows.

## Phase Selection Decision Tree

```
What does the user need?
│
├─ "Why should we build this?" ──────────→ Phase 1: Conceive
│   ├─ Vision, market size, personas
│   └─ Business case, competitive analysis
│
├─ "What should we build and when?" ─────→ Phase 2: Plan
│   ├─ PRD, roadmap, resource plan
│   └─ Risk assessment, success metrics
│
├─ "How do we build it?" ────────────────→ Phase 3: Develop
│   ├─ Architecture, design system, APIs
│   └─ Sprint tracking, changelog
│
├─ "Does it work correctly?" ────────────→ Phase 4: Qualify
│   ├─ Test strategy, QA plan, bug tracking
│   └─ Acceptance criteria, gate checklist
│
├─ "How do we ship it?" ─────────────────→ Phase 5: Launch
│   ├─ GTM, store optimization, beta plan
│   └─ Press/marketing, launch runbook
│
├─ "How do we keep it running?" ─────────→ Phase 6: Deliver
│   ├─ Monitoring, feedback, analytics
│   └─ Enhancement roadmap, incident response
│
└─ "How do we wind it down?" ────────────→ Phase 7: Retire
    ├─ Deprecation, data migration, EOL
    └─ Knowledge archive, lessons learned
```

## Document Quick-Find

| User Says... | Phase | Document |
|--------------|-------|----------|
| "vision", "mission", "why" | 1 | 01-product-vision-statement |
| "market size", "TAM", "opportunity" | 1 | 02-market-opportunity-analysis |
| "competitors", "alternatives" | 1 | 03-competitive-landscape |
| "personas", "users", "JTBD" | 1 | 04-user-personas-and-needs |
| "business case", "ROI", "costs" | 1 | 05-business-case |
| "validation", "feasibility" | 1 | 06-concept-validation-summary |
| "PRD", "requirements", "features" | 2 | 01-product-requirements-document |
| "roadmap", "timeline", "milestones" | 2 | 02-product-roadmap |
| "resources", "capacity", "team" | 2 | 03-resource-and-capacity-plan |
| "risks", "RAID", "mitigation" | 2 | 04-risk-assessment-and-mitigation |
| "KPIs", "metrics", "OKRs" | 2 | 05-success-metrics-and-kpis |
| "stakeholders", "communication" | 2 | 06-stakeholder-communication-plan |
| "architecture", "tech stack" | 3 | 01-technical-architecture-spec |
| "UX", "screens", "user flows" | 3 | 02-ux-design-specifications |
| "design system", "tokens", "components" | 3 | 03-design-system-reference |
| "sprint", "backlog", "progress" | 3 | 04-sprint-backlog-and-progress |
| "API", "endpoints", "integration" | 3 | 05-api-integration-spec |
| "changelog", "versions", "releases" | 3 | 06-development-changelog |
| "QA", "quality", "testing plan" | 4 | 01-quality-assurance-plan |
| "test coverage", "test strategy" | 4 | 02-test-strategy-and-coverage |
| "acceptance criteria" | 4 | 03-acceptance-criteria-matrix |
| "bugs", "defects", "issues" | 4 | 04-bug-tracking-and-resolution |
| "device testing", "real device" | 4 | 05-real-device-test-report |
| "submission checklist", "pre-release" | 4 | 06-pre-submission-gate-checklist |
| "GTM", "go-to-market" | 5 | 01-go-to-market-strategy |
| "ASO", "App Store", "keywords" | 5 | 02-app-store-optimization |
| "launch readiness", "launch checklist" | 5 | 03-launch-readiness-checklist |
| "press", "marketing", "PR" | 5 | 04-press-and-marketing-plan |
| "beta", "TestFlight", "testers" | 5 | 05-beta-program-plan |
| "launch day", "runbook" | 5 | 06-launch-day-runbook |
| "monitoring", "alerts", "dashboards" | 6 | 01-post-launch-monitoring-plan |
| "feedback", "reviews", "NPS" | 6 | 02-customer-feedback-framework |
| "enhancements", "iteration", "v2" | 6 | 03-iteration-and-enhancement-roadmap |
| "support", "operations", "FAQ" | 6 | 04-operational-support-plan |
| "analytics", "reporting", "events" | 6 | 05-analytics-and-reporting-cadence |
| "incident", "outage", "post-mortem" | 6 | 06-incident-response-playbook |
| "deprecation", "sunset" | 7 | 01-feature-deprecation-policy |
| "data migration", "schema" | 7 | 02-data-migration-plan |
| "end of life", "EOL", "retire" | 7 | 03-end-of-life-criteria |
| "user communication", "shutdown notice" | 7 | 04-user-communication-plan |
| "archive", "knowledge transfer" | 7 | 05-knowledge-archive-strategy |
| "lessons learned", "retrospective" | 7 | 06-lessons-learned-template |

## Common Workflows

### Full Suite Generation
1. Read project context (README, source, existing docs)
2. Ask user to confirm scope (all 42 or subset)
3. Create directory structure
4. Generate Phase 1-7 sequentially (6 docs per phase in parallel)
5. Verify with file count (expect 42)

### Single Document
1. Identify which phase and document from the quick-find table
2. Read the relevant phase reference file
3. Scan project for sources to populate the document
4. Generate the document with standard header
5. Place in correct directory

### Audit Mode
1. Glob for existing docs: `docs/**/*.md`
2. Map each to the 42-document matrix
3. Score: completeness (0-10), accuracy (0-10), actionability (0-10)
4. Output gap analysis table with priorities

### Update Existing Suite
1. Read all 42 existing documents
2. Scan codebase for changes since last update
3. Identify which documents need updates
4. Update only changed documents
5. Bump revision history in each updated doc
