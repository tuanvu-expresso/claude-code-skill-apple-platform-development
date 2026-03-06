# Document Templates and Standards

Standard formatting, headers, and conventions for all ProBOK documents.

## Standard Document Header

Every document must begin with this header:

```markdown
# [Document Title]

> **Phase [X] — [Phase Name]** | Document [Y] of 6
> **Project:** [Project Name] | **Version:** [X.Y.Z]
> **Last Updated:** YYYY-MM-DD | **Status:** Draft | Active | Approved

---

## Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | YYYY-MM-DD | [Author] | Initial creation |

---
```

## Cross-Reference Format

Link to related documents using this format:

```markdown
> **Related Documents:**
> - [Phase 1, Doc 3: Competitive Landscape](../01-conceive/03-competitive-landscape.md)
> - [Phase 2, Doc 1: PRD](../02-plan/01-product-requirements-document.md)
```

## Status Definitions

| Status | Meaning |
|--------|---------|
| **Draft** | Initial creation, not yet reviewed |
| **Active** | Approved and in use, may be updated |
| **Approved** | Formally reviewed and locked |
| **Superseded** | Replaced by a newer version |
| **Archived** | No longer maintained |

## Document Quality Checklist

Apply to every document before marking as complete:

- [ ] Header contains accurate project name, version, and date
- [ ] All sections from the phase reference are present
- [ ] Content is project-specific (no generic placeholder text)
- [ ] Tables have real data, not "[TBD]" entries
- [ ] Cross-references point to actual documents
- [ ] Checklists have accurate status (Done/Pending/N/A)
- [ ] Metrics include actual numbers from the project
- [ ] Code references use actual file paths and line numbers
- [ ] No contradictions with other ProBOK documents
- [ ] Revision history is populated

## Tone and Style

- **Voice:** Professional but concise — no filler prose
- **Tense:** Present tense for current state, future tense for plans
- **Specificity:** Always prefer concrete numbers over vague descriptions
  - Bad: "The app has good test coverage"
  - Good: "100 XCTests across 53 unit, 15 integration, and 15 ViewModel tests (87% coverage)"
- **Tables over paragraphs:** Use tables for any structured data
- **Actionable items:** Use checkboxes `- [ ]` for any action items

## File Naming Convention

```
XX-document-name.md
```

Where `XX` is the zero-padded document number (01-06) within the phase.

## Directory Structure

```
docs/product-management-7-phases/
├── 01-conceive/     (01-06)
├── 02-plan/         (01-06)
├── 03-develop/      (01-06)
├── 04-qualify/      (01-06)
├── 05-launch/       (01-06)
├── 06-deliver/      (01-06)
└── 07-retire/       (01-06)
```

## Adapting to Project Type

### Mobile App (iOS/Android)
- Phase 5 focus: App Store Optimization, TestFlight/Internal Testing
- Phase 4 focus: Device matrix testing, accessibility audit
- Phase 6 focus: Crash reporting, app review responses

### Web Application
- Phase 5 focus: SEO, CDN deployment, browser compatibility
- Phase 4 focus: Cross-browser testing, lighthouse scores
- Phase 6 focus: Uptime monitoring, CDN performance

### Backend/API
- Phase 3 focus: API contract documentation, OpenAPI spec
- Phase 5 focus: API versioning strategy, developer documentation
- Phase 6 focus: SLA monitoring, rate limiting, usage dashboards

### CLI Tool
- Phase 5 focus: Package manager distribution (Homebrew, npm, pip)
- Phase 4 focus: Cross-platform testing (Linux, macOS, Windows)
- Phase 6 focus: Backward compatibility, migration guides

### Library/SDK
- Phase 3 focus: Public API surface, documentation generation
- Phase 5 focus: Package registry publishing, sample code
- Phase 7 focus: Semantic versioning, deprecation policy
