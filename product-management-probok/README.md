# Product Management ProBOK — Claude Code Skill

A Claude Code skill that generates comprehensive product management documentation aligned with the **Product Management Body of Knowledge (ProBOK)** 7-phase lifecycle framework. Works across all projects.

## Overview

This skill produces **42 project-specific deliverables** (6 per phase) by analyzing your codebase, existing documentation, git history, and architecture — not generic templates.

| Feature | Detail |
|---------|--------|
| **Trigger** | `/product-management-probok` or any mention of ProBOK, product lifecycle, phase docs |
| **Scope** | Full 42-doc suite, single phase (6 docs), single document, or audit mode |
| **Platform-aware** | Adapts for iOS, Android, Web, Backend, CLI, or Library projects |
| **Project-specific** | Scans source code, existing docs, git history — never generates generic templates |
| **Progressive disclosure** | SKILL.md loads first; phase references load only when needed |
| **Cross-project** | Works on any project in any Claude Code session |

## The 7 Phases

| # | Phase | Focus | Deliverables |
|---|-------|-------|--------------|
| 1 | **Conceive** | Why build this? | Vision, Market Analysis, Competitive Landscape, Personas, Business Case, Concept Validation |
| 2 | **Plan** | How will we build it? | PRD, Roadmap, Resource Plan, Risk Assessment, Success Metrics, Stakeholder Comms |
| 3 | **Develop** | Build it right | Architecture Spec, UX Spec, Design System, Sprint Backlog, API Spec, Changelog |
| 4 | **Qualify** | Prove it works | QA Plan, Test Strategy, Acceptance Matrix, Bug Tracking, Device Testing, Pre-Release Gate |
| 5 | **Launch** | Ship it well | GTM Strategy, Store Optimization, Launch Readiness, Press/Marketing, Beta Program, Launch Runbook |
| 6 | **Deliver** | Keep it running | Post-Launch Monitoring, Feedback Framework, Enhancement Roadmap, Operations, Analytics, Incident Response |
| 7 | **Retire** | Wind down gracefully | Deprecation Policy, Data Migration, EOL Criteria, User Communication, Knowledge Archive, Lessons Learned |

## Usage

### Full Suite (42 documents)

```
/product-management-probok
```

Or simply ask:

> "Generate ProBOK documentation for this project"

### Single Phase (6 documents)

> "Create Phase 4 Qualify documents"

### Single Document

> "Write a go-to-market strategy"
> "Create a risk assessment"
> "Generate the test strategy document"

### Audit Mode

> "Audit my existing docs against ProBOK"

Returns a gap analysis with coverage scores and prioritized recommendations.

## Output Structure

All documents are placed under the project's docs directory:

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

Every generated document includes:

- **Metadata header** — Phase, project name, version, date, status
- **Revision history** — Version table for tracking changes
- **Cross-references** — Links to related documents in other phases
- **Actionable content** — Tables, checklists, decision matrices (not just prose)
- **Project-specific data** — Real file paths, metrics, API endpoints, architecture details

## Platform Adaptations

The skill automatically adapts deliverables based on the project type:

| Platform | Key Adaptations |
|----------|----------------|
| **iOS / macOS** | App Store Optimization, TestFlight Beta, App Review Guidelines, privacy manifests |
| **Android** | Play Store Listing, Internal/Closed/Open Testing Tracks, Play Console |
| **Web App** | SEO Strategy, CDN/Hosting, Browser Compatibility, Lighthouse scores |
| **Backend / API** | API Documentation, SLA Definitions, OpenAPI spec, Migration Guides |
| **CLI Tool** | Package manager distribution, cross-platform testing, man pages |
| **Library / SDK** | Public API surface, semantic versioning, package registry publishing |

## Skill Architecture

```
~/.claude/skills/product-management-probok/
├── SKILL.md                     # Main orchestrator (187 lines)
├── README.md                    # This file
├── quick-ref.md                 # Decision tree & document finder (113 lines)
└── references/
    ├── phase-1-conceive.md      # Vision & validation guide (140 lines)
    ├── phase-2-plan.md          # Planning & requirements guide (144 lines)
    ├── phase-3-develop.md       # Development & architecture guide (148 lines)
    ├── phase-4-qualify.md       # Quality assurance guide (144 lines)
    ├── phase-5-launch.md        # Go-to-market guide (144 lines)
    ├── phase-6-deliver.md       # Operations & growth guide (147 lines)
    ├── phase-7-retire.md        # End-of-life guide (148 lines)
    └── document-templates.md    # Formatting & standards (118 lines)
```

**Progressive disclosure:** Only `SKILL.md` metadata loads into context by default. Phase references and quick-ref load on demand when the relevant phase is being generated.

## Installation

Already installed globally at `~/.claude/skills/`. No additional setup required — the skill is available in every Claude Code session across all projects.

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-03-04 | Initial release — 7 phases, 42 documents, 10 reference files |
