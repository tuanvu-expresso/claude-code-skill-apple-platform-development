# Claude Code Skills for Apple Platform Development

A comprehensive collection of 25 skill modules (421 files) for [Claude Code](https://claude.com/claude-code), covering the full Apple development lifecycle — from idea to App Store.

These skills provide Claude Code with deep, structured knowledge about iOS, macOS, watchOS, visionOS, and tvOS development, enabling it to write better code, review UI against Apple Human Interface Guidelines, generate production-ready components, and guide product decisions.

## Installation

Clone this repo into your Claude Code skills directory:

```bash
# Back up existing skills if needed
mv ~/.claude/skills ~/.claude/skills-backup

# Clone
git clone https://github.com/tuanvu-expresso/claude-code-skill-ios-development.git ~/.claude/skills
```

Skills are automatically detected by Claude Code — no additional configuration required.

## Skills Overview

### Platform Development

| Skill | Description |
|-------|-------------|
| [**ios**](ios/) | iOS development guidance — Swift best practices, SwiftUI patterns, UI/UX review against HIG, navigation architecture, app planning |
| [**macos**](macos/) | macOS development — Swift 6+, SwiftUI, SwiftData, architecture patterns, AppKit bridging, macOS 26 Tahoe APIs |
| [**watchos**](watchos/) | watchOS development — SwiftUI for Watch, Watch Connectivity, complications, watch-specific UI |
| [**visionos**](visionos/) | visionOS development — spatial computing, widgets |
| [**swift**](swift/) | Swift language patterns — concurrency (async/await, actors), memory management, performance, modern idioms |
| [**swiftui**](swiftui/) | SwiftUI-specific skills — AlarmKit, Charts 3D, text editing, toolbars, WebKit integration |
| [**swiftdata**](swiftdata/) | SwiftData patterns — inheritance, schema design |
| [**foundation**](foundation/) | Foundation framework — AttributedString and more |

### Design & UX

| Skill | Description |
|-------|-------------|
| [**apple-hig-principles**](apple-hig-principles/) | Universal Apple HIG principles for all platforms — accessibility, color, typography, layout, navigation, modality, components, platform-specific adaptations |
| [**design**](design/) | Modern Apple design systems — Liquid Glass (iOS 26+), spring/bounce/snappy animations, PhaseAnimator, KeyframeAnimator, SF Symbol effects, view transitions |

### AI & Machine Learning

| Skill | Description |
|-------|-------------|
| [**apple-intelligence**](apple-intelligence/) | Apple Intelligence — Foundation Models, Visual Intelligence, App Intents for Siri |
| [**core-ml**](core-ml/) | Core ML, Create ML, Vision framework, Natural Language framework, on-device ML integration |

### Code Generators

The [**generators**](generators/) module contains 62 production-ready code generators:

<details>
<summary>View all 62 generators</summary>

#### App Infrastructure
| Generator | What it creates |
|-----------|----------------|
| `analytics-setup` | Analytics service with Firebase/TelemetryDeck providers |
| `auth-flow` | Sign in with Apple, biometric auth, Keychain manager |
| `ci-cd-setup` | GitHub Actions, Fastlane, Xcode Cloud pipelines |
| `cloudkit-sync` | CloudKit sync infrastructure |
| `data-export` | User data export (GDPR compliance) |
| `deep-linking` | Universal Links, URL schemes, App Shortcuts |
| `error-monitoring` | Crashlytics/Sentry error monitoring service |
| `feature-flags` | Feature flag system with remote config |
| `force-update` | Forced app update flow |
| `localization-setup` | Localization manager with String Catalogs |
| `logging-setup` | OSLog-based structured logging |
| `networking-layer` | APIClient, endpoints, mock client |
| `offline-queue` | Offline operation queue with retry |
| `persistence-setup` | SwiftData/Core Data persistence with repository pattern |
| `push-notifications` | Push notification manager, categories, delegates |
| `state-restoration` | App state restoration across launches |

#### UI Components
| Generator | What it creates |
|-----------|----------------|
| `accessibility-generator` | Accessibility labels, traits, VoiceOver support |
| `announcement-banner` | In-app announcement banners |
| `debug-menu` | Developer debug menu |
| `feedback-form` | In-app feedback form |
| `image-loading` | Async image loading with caching |
| `onboarding-generator` | Onboarding flow with pages and storage |
| `pagination` | Infinite scroll pagination |
| `settings-screen` | Full settings screen with sections |
| `whats-new` | What's New screen for app updates |

#### Monetization & StoreKit
| Generator | What it creates |
|-----------|----------------|
| `offer-codes-setup` | Offer codes configuration |
| `paywall-generator` | StoreKit 2 paywall with subscription management |
| `promoted-iap` | Promoted in-app purchases |
| `review-prompt` | Smart review prompt timing |
| `subscription-lifecycle` | Subscription status tracking and management |
| `subscription-offers` | Introductory and promotional offers |
| `win-back-offers` | Win-back offer flows for churned users |

#### Engagement & Retention
| Generator | What it creates |
|-----------|----------------|
| `consent-flow` | Privacy consent and opt-in flows |
| `lapsed-user` | Lapsed user re-engagement |
| `milestone-celebration` | Achievement and milestone celebrations |
| `permission-priming` | Pre-permission explanation screens |
| `quick-win-session` | Quick win session patterns |
| `referral-system` | User referral system |
| `streak-tracker` | Streak tracking with rewards |
| `tipkit-generator` | TipKit contextual tips |
| `usage-insights` | Usage analytics and insights dashboard |
| `variable-rewards` | Variable reward mechanics |

#### Sharing & Social
| Generator | What it creates |
|-----------|----------------|
| `share-card` | Shareable card image generation |
| `social-export` | Social media export (Instagram Stories, etc.) |
| `watermark-engine` | Image watermarking |

#### App Extensions & Widgets
| Generator | What it creates |
|-----------|----------------|
| `app-clip` | App Clip target and experience |
| `app-extensions` | App extension targets |
| `background-processing` | Background tasks and processing |
| `live-activity-generator` | Live Activities with ActivityKit |
| `spotlight-indexing` | Spotlight and Core Spotlight indexing |
| `widget-generator` | Home Screen widgets |

#### App Store & Distribution
| Generator | What it creates |
|-----------|----------------|
| `account-deletion` | Account deletion flow (App Store requirement) |
| `app-icon-generator` | App icon asset generation script |
| `app-store-assets` | App Store screenshot and asset specs |
| `custom-product-pages` | Custom product page variants |
| `featuring-nomination` | App Store featuring nomination |
| `http-cache` | HTTP response caching |
| `in-app-events` | App Store in-app events |
| `pre-orders` | Pre-order configuration |
| `product-page-optimization` | A/B testing product pages |
| `screenshot-automation` | Automated screenshot generation |
| `test-generator` | Test scaffolding and templates |

</details>

### Product & Business

| Skill | Description |
|-------|-------------|
| [**product**](product/) | End-to-end product development — market research, competitive analysis, PRD, architecture specs, UX design, implementation guides, beta testing, release specs |
| [**product-management-probok**](product-management-probok/) | ProBOK 7-phase lifecycle — Conceive, Plan, Develop, Qualify, Launch, Deliver, Retire |
| [**monetization**](monetization/) | Pricing strategy — readiness assessment, model selection, tier structuring, free trials |
| [**growth**](growth/) | User acquisition, analytics interpretation, press/media outreach, community building, indie business ops |
| [**app-store**](app-store/) | ASO — descriptions, screenshots, keywords, review responses, marketing strategy, rejection handling |

### Quality & Security

| Skill | Description |
|-------|-------------|
| [**testing**](testing/) | TDD workflows — characterization tests, test contracts, snapshot tests, integration scaffolds, test data factories |
| [**security**](security/) | Security review — secure storage, biometric auth, network security, privacy manifests |
| [**release-review**](release-review/) | Pre-release review — security, privacy, UX, distribution, API design checklists |
| [**performance**](performance/) | Performance profiling — Time Profiler, memory, energy diagnostics, SwiftUI debugging |

### Legal & Compliance

| Skill | Description |
|-------|-------------|
| [**legal**](legal/) | Legal documents — privacy policies, terms of service, EULAs, GDPR/CCPA/DPDP compliance |

### Utilities

| Skill | Description |
|-------|-------------|
| [**shared**](shared/) | Skill creation templates and best practices for building new Claude Code skills |
| [**mapkit**](mapkit/) | MapKit and GeoToolbox patterns |

## How Skills Work

Each skill follows a consistent structure:

```
skill-name/
  SKILL.md          # Main skill definition with triggers and instructions
  sub-module/
    SKILL.md        # Sub-skill definition
    reference.md    # Detailed reference material
    templates/      # Code templates (where applicable)
```

The `SKILL.md` front matter controls when Claude Code activates the skill:

```yaml
---
name: skill-name
description: When and why to use this skill...
allowed-tools: [Read, Write, Edit, Glob, Grep]
---
```

Claude Code automatically loads the relevant skill based on your conversation context — no manual invocation needed.

## Contributing

1. Fork this repository
2. Create your skill following the structure in [shared/skill-creator/](shared/skill-creator/)
3. Submit a pull request

## License

MIT
