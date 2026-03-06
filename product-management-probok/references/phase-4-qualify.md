# Phase 4 — Qualify

> "Prove it works."

The Qualify phase ensures the product meets quality standards before release through systematic testing, bug tracking, and gate checks.

## Deliverable 1: Quality Assurance Plan

### Purpose
Define the overall QA strategy, quality gates, and quality standards.

### Required Sections
1. **Quality Philosophy** — Approach to quality (shift-left, TDD, etc.)
2. **Testing Model** — Tiers of testing (unit, integration, UI, manual)
3. **Quality Gates** — Per-commit, per-release, pre-submission gates with criteria
4. **Coverage Targets** — Code coverage goals by module/layer
5. **Defect Management** — How bugs are reported, triaged, prioritized, fixed
6. **Severity Classification** — S0-S4 or Critical/Major/Minor/Cosmetic definitions
7. **Regression Strategy** — How to prevent regressions
8. **Quality Metrics** — Defect density, escape rate, fix time, test pass rate

### How to Populate
- Check for test targets and test files in the project
- Read existing TESTING_STRATEGY.md or QA docs
- Look for CI/CD configuration (.github/workflows, Fastfile, etc.)
- Scan for lint configuration (SwiftLint, ESLint, etc.)
- Check for code review process (PR templates, CODEOWNERS)

---

## Deliverable 2: Test Strategy and Coverage

### Purpose
Detail the testing pyramid, test suite inventory, and coverage metrics.

### Required Sections
1. **Test Pyramid** — Unit / Integration / E2E distribution
2. **Test Suite Inventory** — All test classes with purpose and count
3. **Test Infrastructure** — Mock objects, factories, helpers, test utilities
4. **Coverage Report** — Current coverage by module (actual numbers)
5. **Gap Analysis** — What's untested and the risk of leaving it untested
6. **Performance Testing** — Load, stress, and performance test strategy
7. **Accessibility Testing** — Accessibility audit process and tools
8. **Platform Testing** — Device matrix, OS version matrix

### How to Populate
- Run `find . -name "*Test*.swift"` or equivalent to inventory tests
- Count test methods per file
- Check for mock/stub/fake classes
- Look for XCTest, Quick/Nimble, or other test frameworks
- Run coverage tool if available and report numbers

---

## Deliverable 3: Acceptance Criteria Matrix

### Purpose
Map every feature to testable acceptance criteria with pass/fail status.

### Required Sections
1. **Criteria by Feature Area** — Grouped by feature/screen
2. **Criteria Format** — Given/When/Then or checklist format
3. **Status Tracking** — Pass / Fail / Deferred / Not Tested per criterion
4. **Coverage Summary** — Total criteria, pass rate, deferred count
5. **Phase-Gated Criteria** — Which criteria are required for which release
6. **Edge Cases** — Boundary conditions and error scenarios
7. **Deferred Rationale** — Why deferred items were postponed

### How to Populate
- Derive criteria from PRD feature requirements
- Cross-reference with test assertions in test files
- Check for BDD-style tests (Given/When/Then patterns)
- Map UI flows to acceptance paths
- Mark items as Pass if corresponding tests pass

---

## Deliverable 4: Bug Tracking and Resolution

### Purpose
Track all known bugs, their severity, resolution status, and patterns.

### Required Sections
1. **Bug Lifecycle** — States: New → Triaged → In Progress → Fixed → Verified → Closed
2. **Severity Definitions** — What qualifies as each severity level
3. **Bug Register** — Table: ID, title, severity, status, root cause, fix, version
4. **Open Issues** — Currently unresolved bugs
5. **Resolved History** — Fixed bugs with lessons learned
6. **Discovery Sources** — Where bugs come from (testing, reviews, production, users)
7. **Pattern Analysis** — Common bug categories and prevention strategies
8. **Regression Candidates** — Fixes that should become regression tests

### How to Populate
- Check GitHub Issues / project issue tracker
- Search codebase for `// BUG:`, `// FIXME:`, `// WORKAROUND:`
- Read CHANGELOG for "fix" entries
- Look for crash reporting SDK integration
- Check git log for commits with "fix", "bug", "crash" in messages

---

## Deliverable 5: Real Device / Environment Test Report

### Purpose
Document testing on actual target devices/environments with findings.

### Required Sections
1. **Test Environment** — Device models, OS versions, network conditions
2. **Test Matrix** — Which scenarios tested on which devices
3. **Test Runs** — Per-run findings with screenshots/evidence
4. **Performance Observations** — Launch time, memory usage, battery impact
5. **Device-Specific Issues** — Problems unique to certain devices/OS versions
6. **Network Condition Testing** — Behavior on slow/offline/intermittent connections
7. **Resolution Status** — Which findings are fixed, deferred, or accepted

### How to Populate
- Check for device-specific conditional code (#available, UIDevice checks)
- Look for network reachability/monitoring code
- Read any existing test reports in docs/
- Check minimum deployment target for OS version range
- Look for @available annotations indicating version-specific code

---

## Deliverable 6: Pre-Submission / Pre-Release Gate Checklist

### Purpose
Final gate before release — every item must be addressed.

### Required Sections
1. **Build & Technical** — Clean build, no warnings, signed, archive succeeds
2. **Store Metadata** — Name, description, keywords, screenshots, privacy URL
3. **Privacy & Compliance** — Privacy manifest, data collection disclosure, consent flows
4. **Quality** — All tests pass, no S0/S1 bugs, performance within targets
5. **Legal** — Terms of service, privacy policy, licenses
6. **Accessibility** — VoiceOver works, Dynamic Type supported, color contrast passes
7. **Checklist Status** — Per-item: Done / Pending / N/A with notes

### How to Populate
- Check for PrivacyInfo.xcprivacy or privacy manifest
- Look for App Store metadata files or fastlane Deliverfile
- Verify signing configuration in project settings
- Check for accessibility modifiers in UI code
- Look for legal documents (LICENSE, TERMS, PRIVACY) in docs/
