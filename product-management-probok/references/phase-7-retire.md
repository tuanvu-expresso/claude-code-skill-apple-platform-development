# Phase 7 — Retire

> "Wind down gracefully."

The Retire phase plans for the end of a product's lifecycle — deprecation, migration, archival, and knowledge preservation. Often overlooked but essential for responsible product management.

## Deliverable 1: Feature Deprecation Policy

### Purpose
Define the process for deprecating features, APIs, or dependencies within the product.

### Required Sections
1. **Deprecation Process** — 3-phase: Announce → Migrate → Remove
2. **Timeline Standards** — Minimum notice periods by impact level
3. **Current Deprecations** — Active deprecations with status and timeline
4. **Future Candidates** — Features or dependencies likely to be deprecated
5. **Communication Requirements** — How users are notified of deprecations
6. **API Provider Evaluation** — Criteria for replacing external data sources
7. **Code Marking Standards** — How deprecated code is marked (@available, comments)
8. **Deprecation Registry** — Living list of all past and current deprecations

### How to Populate
- Search for @available(*, deprecated) or @_deprecated annotations
- Look for "deprecated", "legacy", "old" in comments and variable names
- Check for API migration code (old endpoint → new endpoint)
- Review git history for major dependency swaps
- Look for feature flags controlling sunset features

---

## Deliverable 2: Data Migration Plan

### Purpose
Ensure user data is preserved, migrated, or properly disposed of during transitions.

### Required Sections
1. **Data Inventory** — All data stores: local DB, UserDefaults, keychain, cache, cloud
2. **Schema Migration Strategy** — How database schema evolves across versions
3. **API Provider Migration** — Steps for switching data sources
4. **Local-to-Cloud Migration** — If/when local data moves to a server
5. **Data Export** — How users can export their data
6. **Data Deletion** — How users can request data deletion (GDPR/CCPA)
7. **Migration Testing** — How migrations are validated
8. **Rollback Procedures** — How to reverse a failed migration

### How to Populate
- Check for database model version files (Core Data .xcdatamodeld, SwiftData schemas)
- Look for migration code (NSMigrationManager, custom migration logic)
- Check for UserDefaults keys and their purposes
- Look for Keychain usage
- Review data export/deletion features or privacy compliance code
- Check for cloud sync services (CloudKit, Firebase, custom backend)

---

## Deliverable 3: End-of-Life Criteria

### Purpose
Define the triggers and process for retiring the product entirely.

### Required Sections
1. **EOL Triggers** — Usage, technical, and business thresholds
2. **Decision Framework** — Scoring model for retire vs. maintain decision
3. **EOL Options** — Maintenance mode, open source, graceful shutdown, hard stop
4. **Minimum Viable Support** — What "keeping the lights on" requires
5. **Cost-Benefit Analysis** — Ongoing costs vs. remaining value
6. **Platform Dependencies** — OS/SDK versions that might force retirement
7. **Succession Planning** — Handoff to maintainer, community, or archive
8. **Timeline Template** — Standard retirement timeline (90-day, 180-day)

### How to Populate
- Check minimum deployment target for platform dependency risk
- Calculate annual maintenance cost (API fees, developer certificates, hosting)
- Look for analytics that would indicate declining usage
- Review dependency health (are key libraries maintained?)
- Check for framework deprecations that affect the app

---

## Deliverable 4: User Communication Plan

### Purpose
Plan how to communicate product retirement to users with empathy and clarity.

### Required Sections
1. **Communication Timeline** — T-90, T-60, T-30, T-7, T-0 touchpoints
2. **Channel Strategy** — App Store update notes, in-app message, email, social media
3. **Message Templates** — Per-channel communication templates
4. **User Data Handling** — What happens to user data, export instructions
5. **Alternative Recommendations** — Competing products to suggest
6. **FAQ** — Anticipated questions and answers
7. **Support Transition** — How support is handled during wind-down
8. **Community Transition** — If open-sourcing, community handoff plan

### How to Populate
- Check for in-app messaging infrastructure
- Look for user contact mechanisms (email, push notifications)
- Identify competitors from competitive analysis (Phase 1)
- Review data export capabilities from data migration plan
- Check for community channels (Discord, Slack, forum)

---

## Deliverable 5: Knowledge Archive Strategy

### Purpose
Preserve institutional knowledge so it's useful for future projects.

### Required Sections
1. **Knowledge Assets Inventory** — Code, docs, designs, research, data
2. **Archive Strategy** — Where and how knowledge is preserved
3. **Code Archive** — Repository preservation (tagging, branching, mirroring)
4. **Documentation Archive** — Which docs to preserve and where
5. **External Dependencies** — Documentation of third-party accounts, keys, certificates
6. **Knowledge Transfer Checklist** — What to hand off and to whom
7. **Archival Schedule** — When each category is archived
8. **Retrieval Plan** — How to find archived knowledge when needed

### How to Populate
- Inventory all documentation in the project
- List all external service accounts (API providers, hosting, certificates)
- Check for design assets (Figma links, Sketch files, image assets)
- Review CI/CD configuration for deployment knowledge
- Document environment-specific setup requirements

---

## Deliverable 6: Lessons Learned Template

### Purpose
Capture what worked, what didn't, and patterns transferable to future projects.

### Required Sections
1. **What Went Well** — Successes and their root causes
2. **What Could Improve** — Failures and their root causes
3. **Key Decisions** — Major decisions made and their outcomes
4. **Retrospective by Phase** — Per-ProBOK-phase reflection
5. **Transferable Patterns** — Patterns worth reusing in future projects
6. **Anti-Patterns** — Mistakes to avoid repeating
7. **Tool/Technology Assessment** — What tools worked, what didn't
8. **Recommendations** — Advice for the next project

### How to Populate
- Review git history for major pivots and their motivations
- Analyze CHANGELOG for the evolution of the product
- Check for abandoned code/features that indicate failed experiments
- Review technical debt and bug patterns for systemic issues
- Compile feedback from all retrospectives conducted
