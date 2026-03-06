# HIG Component Guidelines

Universal component usage guidelines from Apple Human Interface Guidelines.

## Buttons

### Button Styles
| Style | Usage |
|-------|-------|
| `.borderedProminent` | Primary action (one per view) |
| `.bordered` | Secondary actions |
| `.borderless` | Tertiary/inline actions |
| `.plain` | Custom-styled buttons |

```swift
// Primary action
Button("Save") { save() }
    .buttonStyle(.borderedProminent)

// Secondary
Button("Cancel") { cancel() }
    .buttonStyle(.bordered)

// Destructive
Button("Delete", role: .destructive) { delete() }
```

### Button Rules
1. One prominent button per view/section
2. Use `role: .destructive` for dangerous actions
3. Use `role: .cancel` for dismiss/cancel actions
4. Button labels: use verbs (Save, Delete, Share) not vague words (OK, Yes)
5. Icon-only buttons MUST have `.accessibilityLabel()`
6. Disable buttons when action unavailable: `.disabled(!isValid)`

---

## Lists & Tables

### List Styles
```swift
List { items }
    .listStyle(.insetGrouped)  // iOS default, grouped sections
    .listStyle(.plain)         // Edge-to-edge rows
    .listStyle(.sidebar)       // macOS/iPad sidebar
    .listStyle(.grouped)       // Grouped without inset
```

### List Best Practices
- Use `Identifiable` items or explicit `id:` parameter
- Provide swipe actions for common operations
- Use `.onDelete` for standard delete gesture
- Use `.onMove` for reordering
- Context menus for additional actions
- Pull-to-refresh with `.refreshable { }`

```swift
List {
    ForEach(items) { item in
        ItemRow(item: item)
            .swipeActions(edge: .trailing) {
                Button("Delete", role: .destructive) { delete(item) }
                Button("Archive") { archive(item) }
                    .tint(.blue)
            }
            .swipeActions(edge: .leading) {
                Button("Pin") { pin(item) }
                    .tint(.yellow)
            }
            .contextMenu {
                Button("Edit") { edit(item) }
                Button("Share") { share(item) }
                Divider()
                Button("Delete", role: .destructive) { delete(item) }
            }
    }
    .onDelete { offsets in deleteItems(at: offsets) }
    .onMove { from, to in moveItems(from: from, to: to) }
}
.refreshable { await loadData() }
```

---

## Controls

### Toggle
```swift
// Standard toggle
Toggle("Airplane Mode", isOn: $airplaneMode)

// With system image
Toggle(isOn: $darkMode) {
    Label("Dark Mode", systemImage: "moon.fill")
}
```

### Slider
```swift
Slider(value: $volume, in: 0...1) {
    Text("Volume")
} minimumValueLabel: {
    Image(systemName: "speaker.fill")
} maximumValueLabel: {
    Image(systemName: "speaker.wave.3.fill")
}
```

### Stepper
```swift
Stepper("Quantity: \(quantity)", value: $quantity, in: 1...99)
```

### Gauge (iOS 16+)
```swift
Gauge(value: progress, in: 0...1) {
    Text("Progress")
} currentValueLabel: {
    Text("\(Int(progress * 100))%")
}
.gaugeStyle(.accessoryCircular)
```

---

## Pickers

### Picker Styles
```swift
// Automatic (context-dependent)
Picker("Sort", selection: $sort) {
    ForEach(SortOption.allCases) { Text($0.name).tag($0) }
}

// Segmented (2-4 short options)
Picker("View", selection: $viewMode) {
    Text("List").tag(ViewMode.list)
    Text("Grid").tag(ViewMode.grid)
}
.pickerStyle(.segmented)

// Menu (inline dropdown)
Picker("Category", selection: $category) {
    ForEach(categories) { Text($0.name).tag($0) }
}
.pickerStyle(.menu)

// Wheel
Picker("Count", selection: $count) {
    ForEach(1...100, id: \.self) { Text("\($0)").tag($0) }
}
.pickerStyle(.wheel)
```

### DatePicker
```swift
// Compact (default)
DatePicker("Date", selection: $date)

// Graphical calendar
DatePicker("Date", selection: $date, displayedComponents: .date)
    .datePickerStyle(.graphical)

// Wheel for time
DatePicker("Time", selection: $time, displayedComponents: .hourAndMinute)
    .datePickerStyle(.wheel)
```

### ColorPicker
```swift
ColorPicker("Accent Color", selection: $color)
```

---

## Menus

### Context Menus
```swift
.contextMenu {
    Button("Copy", systemImage: "doc.on.doc") { copy() }
    Button("Share", systemImage: "square.and.arrow.up") { share() }
    Divider()
    Button("Delete", systemImage: "trash", role: .destructive) { delete() }
}
```

### Menu Button
```swift
Menu("Options") {
    Button("Edit") { }
    Button("Duplicate") { }
    Menu("Move to") {
        Button("Folder 1") { }
        Button("Folder 2") { }
    }
    Divider()
    Button("Delete", role: .destructive) { }
}
```

### Menu Rules
1. Group related actions
2. Use `Divider()` between groups
3. Destructive actions at the bottom, separated by divider
4. Use SF Symbols for visual clarity
5. Use submenus for hierarchical choices (don't nest too deep)

---

## Toolbars

### Toolbar Placement
```swift
.toolbar {
    // iOS: top trailing, macOS: toolbar area
    ToolbarItem(placement: .primaryAction) {
        Button("Add", systemImage: "plus") { }
    }

    // iOS: top leading cancel
    ToolbarItem(placement: .cancellationAction) {
        Button("Cancel") { dismiss() }
    }

    // iOS: top trailing confirm
    ToolbarItem(placement: .confirmationAction) {
        Button("Done") { save() }
    }

    // Bottom toolbar
    ToolbarItem(placement: .bottomBar) {
        Button("Filter", systemImage: "line.3.horizontal.decrease") { }
    }
}
```

### Toolbar Rules
1. Primary action in `.primaryAction` placement
2. Cancel/Done pair for modal views
3. Don't overcrowd - max 3-4 items
4. Use SF Symbols for toolbar buttons
5. Toolbar buttons need accessibility labels

---

## Indicators

### Progress Indicators
```swift
// Indeterminate spinner
ProgressView()

// With label
ProgressView("Loading...")

// Determinate bar
ProgressView(value: 0.7) {
    Text("Uploading")
}

// Circular determinate
ProgressView(value: 0.7)
    .progressViewStyle(.circular)
```

### Activity Indicators
- Use `ProgressView()` (not UIActivityIndicatorView in SwiftUI)
- Place near the content being loaded
- Include descriptive label when space allows
- For full-screen loading, center with explanatory text

---

## Labels & Text

### Label Component
```swift
// SF Symbol + Text (preferred for list items, menus)
Label("Favorites", systemImage: "heart.fill")
Label("Settings", systemImage: "gear")

// Custom image
Label("Profile", image: "custom-icon")
```

### Text Formatting
```swift
// Attributed text
Text("Hello, ") + Text("World").bold()

// Date formatting
Text(date, style: .date)
Text(date, style: .relative)
Text(date, style: .timer)

// Number formatting
Text(price, format: .currency(code: "USD"))
Text(percentage, format: .percent)
```

---

## Presentation

### Sheets
```swift
.sheet(isPresented: $showSheet) {
    SheetContent()
        .presentationDetents([.medium, .large])
        .presentationDragIndicator(.visible)
        .presentationCornerRadius(20)
        .interactiveDismissDisabled(hasUnsavedChanges)
}
```

### Popovers (iPad/Mac)
```swift
.popover(isPresented: $showPopover) {
    PopoverContent()
        .frame(minWidth: 300, minHeight: 200)
}
```

### Full Screen Cover
```swift
.fullScreenCover(isPresented: $showFullScreen) {
    FullScreenContent()
}
```

### Inspector (iOS 17+/macOS)
```swift
.inspector(isPresented: $showInspector) {
    InspectorContent()
        .inspectorColumnWidth(min: 200, ideal: 300, max: 400)
}
```

### Presentation Rules
1. Sheet: focused tasks, forms (dismissible by swipe)
2. Full screen cover: immersive experiences, media playback
3. Popover: contextual info on iPad/Mac (becomes sheet on iPhone)
4. Alert: critical decisions only
5. Confirmation dialog: multiple action choices
6. Always provide explicit dismiss mechanism
7. Use `.interactiveDismissDisabled()` when data loss is possible

---

## Badges & Status

### Badge
```swift
// Tab badge
.badge(unreadCount)

// List row badge
Text("Inbox")
    .badge(5)
```

### Status Indicators
- Use semantic colors for status (green=success, yellow=warning, red=error)
- Combine color with icon or text (never color alone)
- Use SF Symbols for status icons

```swift
HStack {
    Image(systemName: "checkmark.circle.fill")
        .foregroundStyle(.green)
    Text("Connected")
}
.accessibilityElement(children: .combine)
.accessibilityLabel("Status: Connected")
```
