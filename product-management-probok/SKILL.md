---
name: product-management-probok
description: Product Management Body of Knowledge (ProBOK) 7-phase lifecycle documentation generator. Creates comprehensive, project-specific deliverables for Conceive, Plan, Develop, Qualify, Launch, Deliver, and Retire phases. Use when user wants product management docs, ProBOK alignment, lifecycle planning, or phase-specific deliverables for any software project.
allowed-tools: [Read, Write, Edit, Glob, Grep, Bash, WebFetch, WebSearch, AskUserQuestion]
---

# Product Management ProBOK — 7-Phase Lifecycle

Generate comprehensive product management documentation aligned with the Product Management Body of Knowledge (ProBOK) framework. Produces 42 deliverable documents (6 per phase) tailored to any software project.

## When This Skill Activates

Use this skill when the user:
- Asks for ProBOK-aligned documentation
- Wants product management lifecycle documents
- Needs phase-specific deliverables (conceive, plan, develop, qualify, launch, deliver, retire)
- Requests a complete product documentation suite
- Mentions "product lifecycle" or "product management phases"
- Wants to audit existing docs against ProBOK standards
- Needs a specific phase document (e.g., "create a go-to-market strategy")

## The 7 Phases and Their Deliverables

| # | Phase | Focus | 6 Deliverables |
|---|-------|-------|-----------------|
| 1 | **Conceive** | Why build this? | Vision, Market Analysis, Competitive Landscape, Personas, Business Case, Concept Validation |
| 2 | **Plan** | How will we build it? | PRD, Roadmap, Resource Plan, Risk Assessment, Success Metrics, Stakeholder Comms |
| 3 | **Develop** | Build it right | Architecture Spec, UX Spec, Design System, Sprint Backlog, API Spec, Changelog |
| 4 | **Qualify** | Prove it works | QA Plan, Test Strategy, Acceptance Matrix, Bug Tracking, Device Testing, Pre-Release Gate |
| 5 | **Launch** | Ship it well | GTM Strategy, Store Optimization, Launch Readiness, Press/Marketing, Beta Program, Launch Runbook |
| 6 | **Deliver** | Keep it running | Post-Launch Monitoring, Feedback Framework, Enhancement Roadmap, Operations, Analytics, Incident Response |
| 7 | **Retire** | Wind down gracefully | Deprecation Policy, Data Migration, EOL Criteria, User Communication, Knowledge Archive, Lessons Learned |

## Process

### 1. Discover Project Context

Before generating any documents, thoroughly understand the project:

- Read the project's README, CLAUDE.md, and any existing docs
- Scan source code structure (languages, frameworks, architecture)
- Identify the project's current lifecycle stage
- Check for existing product docs that should be incorporated
- Determine the platform (iOS, macOS, web, backend, cross-platform)

### 2. Determine Scope

Ask the user what they need:

- **Full suite**: All 7 phases, 42 documents
- **Single phase**: 6 documents for one specific phase
- **Single document**: One specific deliverable
- **Audit mode**: Compare existing docs against ProBOK standards

### 3. Load Phase References

Read the relevant phase reference files from `references/` in this skill directory:

- `references/phase-1-conceive.md` — Vision and validation deliverables
- `references/phase-2-plan.md` — Planning and requirements deliverables
- `references/phase-3-develop.md` — Development and architecture deliverables
- `references/phase-4-qualify.md` — Quality assurance deliverables
- `references/phase-5-launch.md` — Go-to-market deliverables
- `references/phase-6-deliver.md` — Operations and growth deliverables
- `references/phase-7-retire.md` — End-of-life deliverables
- `references/document-templates.md` — Standard headers and formatting

### 4. Generate Documents

For each document:

1. **Synthesize** from multiple project sources — never copy-paste generic templates
2. **Reflect actual project state** — use real version numbers, file counts, API endpoints, metrics
3. **Cross-reference** related documents across phases
4. **Include revision history** with metadata header
5. **Add actionable items** — checklists, tables, decision matrices

### 5. Output Structure

Place all documents under the project's docs directory:

```
docs/product-management-7-phases/
├── 01-conceive/
│   ├── 01-product-vision-statement.md
│   ├── 02-market-opportunity-analysis.md
│   ├── 03-competitive-landscape.md
│   ├── 04-user-personas-and-needs.md
│   ├── 05-business-case.md
│   └── 06-concept-validation-summary.md
├── 02-plan/
│   ├── 01-product-requirements-document.md
│   ├── 02-product-roadmap.md
│   ├── 03-resource-and-capacity-plan.md
│   ├── 04-risk-assessment-and-mitigation.md
│   ├── 05-success-metrics-and-kpis.md
│   └── 06-stakeholder-communication-plan.md
├── 03-develop/
│   ├── 01-technical-architecture-spec.md
│   ├── 02-ux-design-specifications.md
│   ├── 03-design-system-reference.md
│   ├── 04-sprint-backlog-and-progress.md
│   ├── 05-api-integration-spec.md
│   └── 06-development-changelog.md
├── 04-qualify/
│   ├── 01-quality-assurance-plan.md
│   ├── 02-test-strategy-and-coverage.md
│   ├── 03-acceptance-criteria-matrix.md
│   ├── 04-bug-tracking-and-resolution.md
│   ├── 05-real-device-test-report.md
│   └── 06-pre-submission-gate-checklist.md
├── 05-launch/
│   ├── 01-go-to-market-strategy.md
│   ├── 02-app-store-optimization.md
│   ├── 03-launch-readiness-checklist.md
│   ├── 04-press-and-marketing-plan.md
│   ├── 05-beta-program-plan.md
│   └── 06-launch-day-runbook.md
├── 06-deliver/
│   ├── 01-post-launch-monitoring-plan.md
│   ├── 02-customer-feedback-framework.md
│   ├── 03-iteration-and-enhancement-roadmap.md
│   ├── 04-operational-support-plan.md
│   ├── 05-analytics-and-reporting-cadence.md
│   └── 06-incident-response-playbook.md
└── 07-retire/
    ├── 01-feature-deprecation-policy.md
    ├── 02-data-migration-plan.md
    ├── 03-end-of-life-criteria.md
    ├── 04-user-communication-plan.md
    ├── 05-knowledge-archive-strategy.md
    └── 06-lessons-learned-template.md
```

## Document Standards

Every document must include:

```markdown
# Document Title
> Phase X — [Phase Name] | Document Y of 6
> Project: [Project Name] | Version: [X.Y.Z]
> Last Updated: YYYY-MM-DD | Status: [Draft/Active/Approved]

## Revision History
| Version | Date | Author | Changes |
|---------|------|--------|---------|
```

### Quality Criteria

- **Project-specific**: References real code, APIs, metrics, architecture — never generic filler
- **Cross-referenced**: Links to related documents in other phases
- **Actionable**: Contains tables, checklists, decision matrices — not just prose
- **Current**: Reflects the project's actual state at time of generation
- **Consistent**: Uses same terminology and version numbers across all 42 documents

## Audit Mode

When auditing existing documentation:

1. Scan existing docs directory for any product management documents
2. Map existing docs to the 42-document ProBOK matrix
3. Report coverage: which documents exist, which are missing, which are outdated
4. Score each existing doc on: completeness (0-10), accuracy (0-10), actionability (0-10)
5. Generate a gap analysis with prioritized recommendations

## Platform Adaptations

Adapt deliverables to the project's platform:

| Platform | Launch Doc Adjustments |
|----------|----------------------|
| iOS/macOS | App Store Optimization, TestFlight Beta, App Review Guidelines |
| Android | Play Store Listing, Internal/Closed/Open Testing Tracks |
| Web App | SEO Strategy, CDN/Hosting, Browser Compatibility |
| Backend/API | API Documentation, SLA Definitions, Migration Guides |
| Cross-platform | Per-platform store optimization, unified test strategy |

## Tips

- Start with Phase 1 (Conceive) even for mature projects — it captures rationale
- Use parallel document generation within a phase (6 docs are independent)
- For existing projects, populate documents from code analysis, not assumptions
- Phase 4 (Qualify) is the most code-dependent — scan test files and CI config
- Phase 7 (Retire) is often skipped but critical for long-term maintenance planning
- Always ask the user to review before writing — present the plan first
