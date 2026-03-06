# Phase 3 — Develop

> "Build it right."

The Develop phase documents the technical implementation — architecture, design system, sprint progress, and API contracts.

## Deliverable 1: Technical Architecture Specification

### Purpose
Define the system architecture, patterns, and technical decisions.

### Required Sections
1. **Architecture Overview** — Pattern name and diagram (MVVM, Clean, VIPER, etc.)
2. **Project Structure** — File organization, module boundaries, naming conventions
3. **Data Flow** — How data moves through the system (diagrams)
4. **Navigation Architecture** — Routing/coordination pattern
5. **Persistence Layer** — Local storage strategy (Core Data, SwiftData, SQLite, Realm)
6. **Networking Layer** — API client architecture, caching, retry logic
7. **Concurrency Model** — Threading/async strategy, actor isolation
8. **Security Architecture** — Secrets management, authentication, data protection
9. **Dependency Graph** — Third-party libraries and their roles
10. **Build Configuration** — Schemes, targets, environments

### How to Populate
- Scan source file structure and naming patterns
- Read coordinator/router files for navigation architecture
- Check Package.swift/Podfile/Cartfile for dependencies
- Look for .xcconfig files for build configuration
- Analyze model files for persistence strategy
- Review service layer for networking patterns

---

## Deliverable 2: UX Design Specifications

### Purpose
Document every screen, interaction, and user flow in the product.

### Required Sections
1. **Screen Inventory** — Complete list of screens with descriptions
2. **User Flows** — Key paths through the app (happy path + error states)
3. **Screen Specifications** — Per-screen layout, components, interactions
4. **Interaction Standards** — Gestures, transitions, animations
5. **Error States** — How errors appear and how users recover
6. **Empty States** — What users see when there's no content
7. **Loading States** — Skeleton screens, spinners, progressive loading
8. **Accessibility Standards** — VoiceOver, Dynamic Type, color contrast

### How to Populate
- List all View files to build screen inventory
- Trace navigation destinations for user flows
- Check for EmptyState/LoadingState/ErrorState components
- Review accessibility modifiers (.accessibilityLabel, .dynamicTypeSize)
- Look for animation code (.animation, withAnimation, .transition)

---

## Deliverable 3: Design System Reference

### Purpose
Catalog all design tokens, components, and visual standards.

### Required Sections
1. **Color Palette** — All colors with hex values, semantic names, usage context
2. **Typography Scale** — Font styles, sizes, weights, line heights
3. **Spacing Scale** — Spacing tokens and their values
4. **Corner Radii** — Border radius tokens
5. **Shadow Definitions** — Shadow styles with parameters
6. **Component Library** — All reusable UI components with props/variants
7. **View Modifiers** — Custom modifiers and their usage
8. **Iconography** — Icon set, naming convention, sizes
9. **Haptic Feedback** — Haptic patterns and when to use them
10. **Motion/Animation** — Standard animation curves and durations

### How to Populate
- Read DesignSystem* files for tokens (colors, spacing, typography)
- Scan for custom ViewModifier definitions
- List all reusable component files
- Check for SF Symbol usage patterns
- Look for haptic feedback calls (UIImpactFeedbackGenerator, etc.)

---

## Deliverable 4: Sprint Backlog and Progress

### Purpose
Track development progress against planned work items.

### Required Sections
1. **Epic Overview** — All epics with item counts and completion percentage
2. **Current Sprint** — Active sprint items with status
3. **Completed Sprints** — Historical sprint summaries
4. **Backlog** — Prioritized list of upcoming work
5. **Burndown/Burnup** — Visual progress tracking
6. **Velocity Trend** — Points/items completed per sprint
7. **Blockers** — Current impediments
8. **Technical Debt** — Known debt items and remediation priority

### How to Populate
- Read PM_TODO or project board for backlog items
- Count completed vs. remaining items
- Check for TODO/FIXME/HACK comments as tech debt indicators
- Analyze git log for sprint-like release patterns
- Map open issues to blocked items

---

## Deliverable 5: API Integration Specification

### Purpose
Document all external API integrations, contracts, and error handling.

### Required Sections
1. **API Overview** — All external services used and their purpose
2. **Authentication** — How each API is authenticated (API keys, OAuth, etc.)
3. **Endpoint Catalog** — Per-API: endpoints, methods, parameters, responses
4. **Data Mapping** — How API responses map to local models
5. **Error Handling** — Error codes, retry logic, fallback behavior
6. **Rate Limits** — Per-API rate limits and how they're managed
7. **Cost Model** — Per-API pricing and usage projections
8. **Migration Notes** — Previous API providers and migration history

### How to Populate
- Read Service files for API endpoint definitions
- Check for URLSession/Alamofire/networking code
- Look for API key configuration in .xcconfig or environment
- Scan error enums for known error types
- Check for retry/backoff logic in network layer

---

## Deliverable 6: Development Changelog

### Purpose
Comprehensive version history documenting what shipped in each release.

### Required Sections
1. **Version History** — Per-version: date, summary, features, fixes, breaking changes
2. **Release Statistics** — Total releases, cadence, lines of code per release
3. **Migration Notes** — Breaking changes that require user action
4. **Known Issues per Version** — What shipped with known problems
5. **Rollback Procedures** — How to revert to previous versions

### How to Populate
- Read existing CHANGELOG.md
- Analyze git tags and release branches
- Count file/line changes per release using git diff
- Check for migration code (database schema versions, etc.)
