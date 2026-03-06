# HIG Foundations

Core design foundations from Apple Human Interface Guidelines applicable to all platforms.

## Accessibility

### Inclusive Design (Non-Negotiable)
Every app must be accessible. Accessibility is not optional or a nice-to-have.

#### VoiceOver Support
- Every interactive element MUST have an accessibility label
- Decorative images: `.accessibilityHidden(true)`
- Meaningful images: `.accessibilityLabel("description")`
- Complex controls: `.accessibilityHint("describes result of action")`
- Group related elements: `.accessibilityElement(children: .combine)`

```swift
// REQUIRED for icon-only buttons
Button(action: addItem) {
    Image(systemName: "plus")
}
.accessibilityLabel("Add item")

// Group related content
HStack {
    Image(systemName: "star.fill")
    Text("4.5")
}
.accessibilityElement(children: .combine)
.accessibilityLabel("Rating: 4.5 stars")
```

#### Dynamic Type
- ALWAYS use system text styles or relative sizes
- NEVER use fixed font sizes for user-facing text
- Test at ALL Dynamic Type sizes including accessibility sizes
- Layouts must adapt to larger text without truncation of essential content

```swift
// CORRECT - Adapts to user preference
Text("Title").font(.headline)
Text("Body").font(.body)
Text("Caption").font(.caption)

// CORRECT - Relative sizing
Text("Custom").font(.system(.body, design: .rounded))

// WRONG - Fixed size ignores user preference
Text("Bad").font(.system(size: 16))
```

#### Color & Contrast
- Minimum contrast ratios: 4.5:1 normal text, 3:1 large text (18pt+), 3:1 UI components
- NEVER convey information by color alone - use icons, shapes, or labels too
- Support "Increase Contrast" accessibility setting
- Support "Reduce Transparency" setting

#### Motion
- Respect "Reduce Motion" preference via `@Environment(\.accessibilityReduceMotion)`
- Provide alternative transitions when motion is reduced
- Auto-playing animations must be pausable

```swift
@Environment(\.accessibilityReduceMotion) var reduceMotion

withAnimation(reduceMotion ? .none : .spring()) {
    // animate
}
```

#### Other Accessibility Features
- Support Bold Text preference
- Support Switch Control navigation
- Provide keyboard shortcuts (iPad/Mac)
- Support Smart Invert Colors (mark images with `.accessibilityIgnoresInvertColors()`)

---

## Color

### Semantic Colors (Always Preferred)
Use semantic colors that adapt automatically to light/dark mode and accessibility settings.

```swift
// PRIMARY USE - Semantic colors
.foregroundStyle(.primary)          // Main text
.foregroundStyle(.secondary)        // Secondary text
.foregroundStyle(.tertiary)         // Tertiary text
.background(Color(.systemBackground))
.background(Color(.secondarySystemBackground))
.background(Color(.tertiarySystemBackground))

// SYSTEM COLORS - Automatically adapt
Color(.systemRed)
Color(.systemBlue)
Color(.systemGreen)

// NEVER hardcode for adaptive contexts
.foregroundColor(.black)  // Breaks in dark mode
.background(.white)       // Breaks in dark mode
```

### Color Roles
- **Accent color**: Brand identity, interactive elements. Set in asset catalog.
- **Semantic colors**: `.primary`, `.secondary` for text hierarchy
- **System colors**: `Color(.systemRed)` for status/meaning
- **Custom colors**: Define in asset catalog with light/dark/high-contrast variants
- **Tint colors**: Use `.tint()` for interactive element coloring

### Dark Mode
- ALWAYS support dark mode - it is expected on all Apple platforms
- Test in both appearances
- Custom colors MUST have dark mode variants in asset catalog
- Elevated surfaces use lighter backgrounds in dark mode

### High Contrast
- Provide high contrast color variants in asset catalog
- Test with Accessibility Inspector's contrast checker

---

## Typography

### Text Styles Hierarchy (Largest to Smallest)
| Style | Usage |
|-------|-------|
| `.largeTitle` | Top-level screen titles |
| `.title` | Section titles |
| `.title2` | Subsection titles |
| `.title3` | Tertiary titles |
| `.headline` | Emphasized body text, row titles |
| `.subheadline` | Secondary row text, labels |
| `.body` | Main content text (default) |
| `.callout` | Callout text, secondary info |
| `.footnote` | Footer text, timestamps |
| `.caption` | Small annotations |
| `.caption2` | Smallest text |

### Typography Rules
1. Use system text styles for Dynamic Type support
2. Limit to 2-3 text styles per view for visual clarity
3. Use font weight to create emphasis within a style
4. Prefer `.font(.headline)` over manual bold + size
5. Custom fonts: register and map to text styles for Dynamic Type

```swift
// Proper hierarchy
VStack(alignment: .leading) {
    Text("Section Title").font(.title2)
    Text("Description").font(.body).foregroundStyle(.secondary)
    Text("Updated 2h ago").font(.caption).foregroundStyle(.tertiary)
}
```

### Text Rendering
- Use `.lineLimit(nil)` sparingly - prefer defined limits with `.truncationMode()`
- Use `Text` interpolation for attributed text
- Multi-line text: left-aligned for readability (LTR languages)
- Use `.textSelection(.enabled)` for copyable text

---

## Layout

### Spacing System
- Use consistent spacing values (multiples of 4 or 8)
- `.padding()` for standard insets (16pt)
- `.padding(.small)` or explicit values for tighter spacing
- `VStack(spacing:)` and `HStack(spacing:)` for internal spacing

### Safe Areas
- ALWAYS respect safe areas for interactive content
- Only ignore safe areas for backgrounds, media, or full-bleed content
- Use `.safeAreaInset()` for persistent bottom/top bars

```swift
// Background extends, content stays safe
ZStack {
    Color.accentColor.ignoresSafeArea()
    VStack { content }
}

// Persistent bottom bar
.safeAreaInset(edge: .bottom) {
    ActionBar()
        .background(.ultraThinMaterial)
}
```

### Tap / Touch Targets
- iOS: Minimum 44x44 points
- watchOS: Minimum 40x40 points (prefer full-width)
- macOS: Minimum 24x24 points for click targets
- Always add padding to small interactive elements

```swift
// Ensure minimum tap target
Button(action: action) {
    Image(systemName: "xmark")
        .frame(minWidth: 44, minHeight: 44)
}
```

### Adaptive Layout
- Use `ViewThatFits` for size-adaptive content
- Use `@Environment(\.horizontalSizeClass)` for layout adaptation
- Support all device sizes including iPad multitasking
- Use `GeometryReader` sparingly - prefer layout containers

```swift
// Adapt to available space
ViewThatFits {
    HStack { labels }
    VStack { labels }
}
```

---

## Icons & Images

### SF Symbols (Preferred)
- Use SF Symbols for all standard iconography
- Consistent with platform style automatically
- Support Dynamic Type, accessibility, and localization
- Use rendering modes appropriately:

```swift
// Monochrome - single color, most common
Image(systemName: "heart.fill")

// Hierarchical - depth with opacity layers
Image(systemName: "square.and.arrow.up")
    .symbolRenderingMode(.hierarchical)

// Palette - custom multi-color
Image(systemName: "person.crop.circle.badge.plus")
    .symbolRenderingMode(.palette)
    .foregroundStyle(.blue, .gray)

// Multicolor - Apple-defined colors
Image(systemName: "externaldrive.badge.icloud")
    .symbolRenderingMode(.multicolor)
```

### Symbol Effects (iOS 17+)
```swift
Image(systemName: "bell")
    .symbolEffect(.bounce, value: notificationCount)
    .symbolEffect(.pulse, isActive: isLoading)
```

### Image Best Practices
- Provide @1x, @2x, @3x assets or use vector PDFs
- Use asset catalogs for theme-adaptive images
- Set accessibility labels on meaningful images
- Use `.resizable()` and `.aspectRatio(contentMode:)` properly

---

## Materials & Translucency

### System Materials
Use system materials for surfaces that overlay content:

```swift
.background(.ultraThinMaterial)   // Most transparent
.background(.thinMaterial)
.background(.regularMaterial)     // Default
.background(.thickMaterial)
.background(.ultraThickMaterial)  // Most opaque
```

### Usage Guidelines
- Toolbars and tab bars: thin or regular material
- Overlays and floating panels: regular material
- Full-screen overlays: thick material
- Respect "Reduce Transparency" - materials become opaque

---

## Motion & Animation

### Animation Principles
1. Animations should be **purposeful** - they communicate, not decorate
2. Animations should be **responsive** - immediate reaction to user input
3. Animations should be **natural** - use spring physics, not linear timing

### Spring Animations (Preferred)
```swift
// Default spring - good for most cases
withAnimation(.spring()) { change() }

// Snappy - quick, minimal bounce
withAnimation(.snappy) { change() }

// Bouncy - playful, more bounce
withAnimation(.bouncy) { change() }

// Custom spring
withAnimation(.spring(duration: 0.3, bounce: 0.2)) { change() }
```

### Transition Guidelines
- Matched geometry for shared elements between views
- Use `.transition()` for appearing/disappearing content
- Navigation transitions should feel spatial and directional
- Always respect Reduce Motion preference
