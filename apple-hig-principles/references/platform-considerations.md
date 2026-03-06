# HIG Platform-Specific Considerations

How universal HIG principles adapt to each Apple platform.

## iOS

### Design Themes
- **Direct manipulation**: Touch-based, gesture-driven interaction
- **Full-screen content**: Content fills the display edge-to-edge
- **Flat hierarchy**: Minimize navigation depth

### Key Requirements
- Support all iPhone screen sizes (SE through Pro Max)
- Support Dynamic Island on Pro models
- Support both orientations unless strongly single-orientation
- 44x44pt minimum tap targets
- Support keyboard shortcuts when external keyboard connected
- Support multitasking (Slide Over, Split View) on iPad

### iOS-Specific Patterns
- Tab bar at bottom for primary navigation
- Pull-to-refresh for updatable content
- Swipe gestures for navigation and actions
- Edge swipe for back navigation (never disable)
- Home indicator area - avoid placing controls near bottom edge
- Status bar - respect and don't obscure

### iOS-Specific Components
- `NavigationStack` with large titles
- `TabView` at bottom
- `.sheet()` with presentation detents
- Swipe actions on list rows
- Context menus with previews

```swift
// iOS idiom
NavigationStack {
    List { content }
        .navigationTitle("Items")
        .navigationBarTitleDisplayMode(.large)
        .refreshable { await refresh() }
}
```

---

## macOS

### Design Themes
- **Indirect manipulation**: Mouse/trackpad with precise pointing
- **Multiple windows**: Users expect to open multiple windows
- **Menu bar**: Full menu bar with keyboard shortcuts
- **Density**: More information density than iOS

### Key Requirements
- Support window resizing (set reasonable min/max sizes)
- Full menu bar with standard menus (File, Edit, View, Window, Help)
- Keyboard shortcuts for all common actions
- Support trackpad gestures
- Right-click context menus
- Toolbar customization
- Support full screen mode
- Respect system accent color

### macOS-Specific Patterns
- Sidebar navigation (`NavigationSplitView`)
- Inspector panels
- Sheets attached to windows (not full-screen)
- Preferences/Settings window (`Settings` scene)
- Toolbar with customizable items
- Touch Bar support (where applicable)

### macOS-Specific Components
- `NavigationSplitView` (two or three column)
- `.toolbar` with labeled items
- `Table` for data-heavy views
- `MenuBarExtra` for menu bar utilities
- Window management with `WindowGroup`, `Window`

```swift
// macOS idiom
NavigationSplitView {
    List(selection: $selection) { sidebar }
        .navigationSplitViewColumnWidth(min: 200, ideal: 250)
} detail: {
    DetailView(item: selection)
        .toolbar {
            ToolbarItem { Button("Add", systemImage: "plus") { } }
        }
}
```

### macOS Sizing
- Minimum click target: 24x24 points
- Standard control heights maintained
- Respect content hugging - don't stretch controls unnecessarily
- Dense layouts acceptable - users have precise pointing

---

## watchOS

### Design Themes
- **Glanceable**: Information at a glance, quick interactions
- **Brief interactions**: Most sessions are under 10 seconds
- **Wrist-friendly**: Optimize for small screen, limited input
- **Health and fitness focus**: Leverage watch sensors

### Key Requirements
- Support all Apple Watch sizes (41mm through 49mm Ultra)
- 40x40pt minimum tap targets (prefer full-width buttons)
- Keep text concise - every word counts
- Support Digital Crown for scrolling and value input
- Prioritize complications for quick access
- Support Always-On Display (dimmed state)
- Minimize scrolling depth

### watchOS-Specific Patterns
- Vertical scrolling lists (primary navigation)
- Page-based navigation with `TabView(.page)`
- Digital Crown input for value selection
- Haptic feedback for confirmations
- Notifications as primary entry point
- Complications for quick data

### watchOS-Specific Components
- Full-width buttons
- `.containerBackground()` for watch backgrounds
- `.digitalCrownRotation()` for value input
- Inline navigation (minimal hierarchy depth)

```swift
// watchOS idiom
NavigationStack {
    List {
        ForEach(items) { item in
            NavigationLink(value: item) {
                HStack {
                    Text(item.name).font(.headline)
                    Spacer()
                    Text(item.value).font(.caption).foregroundStyle(.secondary)
                }
            }
        }
    }
    .navigationTitle("Activity")
}
```

### Always-On Display
- Reduce visual complexity in always-on state
- Remove animations
- Dim colors (reduce saturation and brightness)
- Hide sensitive information
- Use `TimelineView` for time-based updates

---

## visionOS

### Design Themes
- **Spatial**: Content exists in 3D space around the user
- **Immersive**: Range from shared space to full immersion
- **Eyes and hands**: Eye tracking for targeting, hand gestures for interaction
- **Comfort**: Avoid visual fatigue, respect personal space

### Key Requirements
- Use glass material (`.glassBackgroundEffect()`) for windows
- Support eye tracking - targets must be large enough
- Support hand gesture interaction
- Design for variable distances (content may be near or far)
- Consider field of view placement
- Support both Shared Space and Full Space

### visionOS-Specific Patterns
- Windows as floating panels in space
- Volumes for 3D content
- Ornaments for contextual controls
- Immersive spaces for AR/VR experiences
- Spatial audio for feedback

### visionOS-Specific Components
- `.glassBackgroundEffect()` on windows
- `RealityView` for 3D content
- `.ornament()` for floating controls
- `ImmersiveSpace` for immersive experiences
- Hover effects for eye-tracking feedback

```swift
// visionOS idiom
WindowGroup {
    ContentView()
        .glassBackgroundEffect()
}

// Ornament
.ornament(attachmentAnchor: .scene(.bottom)) {
    HStack {
        Button("Play", systemImage: "play.fill") { }
        Button("Stop", systemImage: "stop.fill") { }
    }
    .padding()
    .glassBackgroundEffect()
}
```

### Spatial Design Guidelines
- Place primary content at eye level, slightly below center of view
- Keep interactive elements within comfortable reach
- Use depth sparingly - excessive depth causes fatigue
- Minimum target size: 60x60 points for indirect interaction
- Provide hover states for eye-tracking feedback

---

## tvOS

### Design Themes
- **Lean-back experience**: Relaxed viewing from a distance
- **Focus-based**: Navigation via focus system, not touch
- **10-foot UI**: Designed to be readable from across a room
- **Shared experience**: Multiple viewers

### Key Requirements
- Large text readable from 10+ feet
- Focus-based navigation (no touch)
- Support Siri Remote gestures
- Top Shelf integration
- Large artwork and imagery
- Simple, predictable navigation

### tvOS-Specific Patterns
- Focus system for navigation
- Top Shelf for app showcase
- Full-screen media playback
- Grid-based content browsing
- Tab bar at top of screen

---

## Cross-Platform Adaptation Principles

### 1. Shared Logic, Platform UI
- Share data models and business logic
- Build platform-native UI for each target
- Use `#if os()` for platform-specific code sparingly

### 2. Respect Platform Idioms
- Don't make an iOS app look the same on macOS
- Each platform has distinct interaction patterns
- Users expect platform-native behavior

### 3. Appropriate Information Density
- watchOS: Minimal, glanceable
- iOS: Comfortable, touch-friendly
- macOS: Dense, mouse-optimized
- visionOS: Spatial, comfortable distance
- tvOS: Large, readable from distance

### 4. Input Method Awareness
- iOS/watchOS: Touch + Digital Crown
- macOS: Mouse/trackpad + keyboard
- visionOS: Eyes + hands + voice
- tvOS: Remote + focus system

```swift
// Platform-adaptive view
struct AdaptiveLayout: View {
    #if os(macOS)
    var body: some View {
        NavigationSplitView { sidebar } detail: { detail }
    }
    #elseif os(watchOS)
    var body: some View {
        NavigationStack { compactList }
    }
    #else // iOS
    var body: some View {
        TabView { tabs }
    }
    #endif
}
```
