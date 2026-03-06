---
name: apple-hig-principles
description: Apple Human Interface Guidelines principles applicable to all Apple platforms (iOS, macOS, watchOS, visionOS, tvOS). Use when reviewing UI/UX, designing interfaces, implementing new features, or ensuring HIG compliance across any Apple project. Activates on mentions of HIG, design review, UI principles, user experience, or Apple design standards.
allowed-tools: [Read, Write, Edit, Glob, Grep, WebFetch, AskUserQuestion]
---

# Apple Human Interface Guidelines - Universal Principles

Cross-platform design principles from Apple's Human Interface Guidelines that apply to ALL Apple platform projects. This skill ensures every UI decision aligns with Apple's design philosophy.

## When This Skill Activates

Use this skill when the user:
- Asks about Apple design principles or HIG compliance
- Requests UI/UX review for any Apple platform
- Is designing or implementing a new feature with UI
- Wants to ensure design consistency across platforms
- Mentions design patterns, visual hierarchy, or user experience
- Asks about accessibility, typography, color, layout, or interaction patterns
- Is building a new app and needs design direction

## How to Use

1. Read relevant reference files from `references/` based on the user's needs
2. Apply principles to the user's specific platform and context
3. Provide concrete, actionable guidance with code examples
4. Reference official Apple documentation when appropriate

## Available References

### references/foundations.md
Core design foundations: accessibility, color, typography, layout, icons, materials, motion, and spatial relationships.

### references/patterns.md
Interaction patterns: navigation, data entry, search, modality, onboarding, feedback, managing content, and offering help.

### references/platform-considerations.md
Platform-specific adaptations: how universal principles manifest differently on iOS, macOS, watchOS, visionOS, and tvOS.

### references/component-guidelines.md
Component-level guidance: buttons, menus, lists, controls, pickers, indicators, and presentation elements.

## Core Design Themes

### 1. Clarity
- Text is legible at every size
- Icons are precise and clear
- Adornments are subtle and appropriate
- Functionality drives design
- Negative space, color, fonts, and graphics highlight important content

### 2. Deference
- Content fills the screen
- Translucency and blurring hint at more
- Minimal use of bezels, gradients, and drop shadows
- The UI helps users understand and interact with content without competing with it

### 3. Depth
- Distinct visual layers convey hierarchy
- Transitions provide a sense of depth
- Touch and discoverability heighten delight and enable access to functionality and additional content

## Review Process

When reviewing code or designs against HIG:

1. **Load references** - Read the relevant reference files for the review context
2. **Check foundations** - Typography, color, spacing, accessibility
3. **Verify patterns** - Navigation, modality, feedback, data entry
4. **Platform compliance** - Platform-specific requirements
5. **Component usage** - Correct component selection and configuration

## Output Format

### Compliant
- List items that follow HIG well
- Highlight good design decisions

### Issues Found
- Specific file:line references
- Description of the HIG violation
- Which HIG principle is violated
- Suggested fix with code example

### Recommendations
- Improvements that would elevate the design
- Platform-specific enhancements
- Accessibility improvements

## Reference Links

- [Apple HIG](https://developer.apple.com/design/human-interface-guidelines)
- [iOS Design](https://developer.apple.com/design/human-interface-guidelines/designing-for-ios)
- [macOS Design](https://developer.apple.com/design/human-interface-guidelines/designing-for-macos)
- [watchOS Design](https://developer.apple.com/design/human-interface-guidelines/designing-for-watchos)
- [visionOS Design](https://developer.apple.com/design/human-interface-guidelines/designing-for-visionos)
- [Accessibility](https://developer.apple.com/accessibility/)
- [SF Symbols](https://developer.apple.com/sf-symbols/)
