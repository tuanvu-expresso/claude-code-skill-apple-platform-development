# Phase 6 — Deliver

> "Keep it running and growing."

The Deliver phase covers post-launch operations — monitoring, feedback loops, iterative improvement, and incident response.

## Deliverable 1: Post-Launch Monitoring Plan

### Purpose
Define what to monitor, how to detect issues, and alert thresholds.

### Required Sections
1. **Monitoring Stack** — Tools and services used for monitoring
2. **Health Dashboard** — Key metrics displayed in real-time
3. **Alert Thresholds** — Per-metric: warning and critical thresholds
4. **Severity Levels** — P0 (critical) through P4 (informational) definitions
5. **API/Service Monitoring** — External dependency health tracking
6. **Performance Baselines** — Expected values for launch time, memory, battery
7. **Usage Projections** — Expected traffic/API usage patterns
8. **Monitoring Cadence** — Daily/weekly review schedule

### How to Populate
- Check for monitoring SDKs (Firebase, DataDog, New Relic, OSLog)
- Look for performance measurement code (os_signpost, MetricKit)
- Check for API usage tracking or quota management code
- Review error logging patterns in the codebase
- Look for health check endpoints or heartbeat mechanisms

---

## Deliverable 2: Customer Feedback Framework

### Purpose
Systematize how user feedback is collected, analyzed, and acted upon.

### Required Sections
1. **Feedback Channels** — All channels: App Store reviews, support email, in-app, social
2. **Collection Methods** — Active (surveys, prompts) vs. passive (analytics, crashes)
3. **Triage Process** — How feedback is categorized and prioritized
4. **Response Templates** — Pre-written responses for common feedback types
5. **Theme Tracking** — How recurring themes are identified and escalated
6. **Sentiment Analysis** — How overall sentiment is tracked over time
7. **Feedback-to-Feature Pipeline** — How feedback becomes backlog items
8. **Escalation Matrix** — When feedback requires immediate action

### How to Populate
- Check for in-app feedback mechanisms (feedback forms, shake-to-report)
- Look for App Store review prompt timing (SKStoreReviewController)
- Check for support email configuration
- Look for analytics events that track user satisfaction
- Check for NPS/CSAT measurement code

---

## Deliverable 3: Iteration and Enhancement Roadmap

### Purpose
Plan the post-launch evolution of the product based on data and feedback.

### Required Sections
1. **Enhancement Pipeline** — Categorized feature requests and improvements
2. **Phase/Version Planning** — What ships in v2.0, v2.1, v3.0, etc.
3. **Prioritization Framework** — Scoring model (impact, effort, strategic value)
4. **Iteration Cadence** — How often new versions ship
5. **Decision Framework** — How enhancement decisions are made
6. **Technical Debt Remediation** — Planned refactoring and cleanup
7. **Platform Updates** — Adopting new OS features and APIs
8. **Deprecation Candidates** — Features that may be removed

### How to Populate
- Read existing roadmap or PM_TODO for planned features
- Check for TODO/FIXME comments indicating desired improvements
- Look for feature flag infrastructure suggesting incremental rollout
- Analyze the gap between current features and competitor features
- Check for platform version checks indicating planned API adoption

---

## Deliverable 4: Operational Support Plan

### Purpose
Define how the product is supported post-launch with minimal overhead.

### Required Sections
1. **Support Model** — Self-service, community, or dedicated support
2. **Known Issues** — Current known issues with workarounds
3. **FAQ** — Frequently asked questions and answers
4. **Update Workflow** — How app updates are prepared, tested, and released
5. **Dependency Monitoring** — Tracking third-party service status
6. **Data Backup** — User data protection and recovery procedures
7. **Compliance Maintenance** — Ongoing privacy/security requirements
8. **Cost Monitoring** — Tracking operational costs against budget

### How to Populate
- Check for FAQ or help documentation in the project
- Look for background sync or data backup code
- Review dependency list for services that require monitoring
- Check for compliance-related code (privacy manifests, consent flows)
- Look for cost-related configuration (API tier, usage limits)

---

## Deliverable 5: Analytics and Reporting Cadence

### Purpose
Define the analytics implementation and regular reporting rhythm.

### Required Sections
1. **Analytics Stack** — Tools and SDKs used
2. **Event Catalog** — All tracked events with parameters and trigger conditions
3. **Implementation Status** — Which events are implemented vs. planned
4. **Privacy Approach** — Data minimization, anonymization, consent
5. **Report Templates** — Weekly, biweekly, monthly report formats
6. **Dashboard Design** — Key metrics and visualizations
7. **Cohort Analysis** — How user cohorts are defined and tracked
8. **Experiment Framework** — How A/B tests are designed and measured

### How to Populate
- Search for analytics SDK imports (Firebase, Amplitude, Mixpanel, TelemetryDeck)
- Grep for tracking/logging calls throughout the codebase
- Check for A/B test infrastructure or feature flag service
- Look for privacy manifest or ATT (App Tracking Transparency) code
- Review existing analytics documentation

---

## Deliverable 6: Incident Response Playbook

### Purpose
Predefined procedures for handling production incidents by severity.

### Required Sections
1. **Severity Definitions** — SEV-1 through SEV-4 with examples
2. **Response Time Targets** — Per-severity: acknowledge, mitigate, resolve
3. **On-Call Structure** — Who responds and when
4. **Incident Procedures** — Step-by-step for each severity level
5. **Specific Scenarios** — Playbooks for likely incidents (crash spike, API outage, data loss)
6. **Communication Templates** — Status page updates, user notifications
7. **Post-Mortem Template** — Root cause analysis format
8. **Escalation Paths** — When to involve additional people/vendors

### How to Populate
- Identify the most likely failure modes from architecture analysis
- Check for graceful degradation patterns in error handling
- Look for retry/fallback logic in network layer
- Review external dependencies for their status page URLs
- Check for feature flags that can disable broken features
