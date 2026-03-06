# HIG Interaction Patterns

Universal interaction patterns from Apple Human Interface Guidelines.

## Navigation

### Hierarchical Navigation
- Use for content with clear parent-child relationships
- NavigationStack (iOS 16+) replaces NavigationView
- Show clear path via navigation titles
- Support swipe-back gesture (do not disable)

```swift
NavigationStack {
    List(categories) { category in
        NavigationLink(value: category) {
            Label(category.name, systemImage: category.icon)
        }
    }
    .navigationTitle("Categories")
    .navigationDestination(for: Category.self) { category in
        CategoryDetailView(category: category)
    }
}
```

### Flat Navigation (Tabs)
- Use TabView for top-level sections (3-5 tabs max)
- Each tab maintains its own navigation state
- Tabs should represent distinct, parallel categories
- Use SF Symbols for tab icons

```swift
TabView {
    HomeView()
        .tabItem { Label("Home", systemImage: "house") }
    SearchView()
        .tabItem { Label("Search", systemImage: "magnifyingglass") }
    ProfileView()
        .tabItem { Label("Profile", systemImage: "person") }
}
```

### Content-Driven Navigation
- Use for experiences where content itself leads to other content
- Common in media, reading, and browsing apps
- Maintain clear path back to origin

### Navigation Principles
1. Always provide a clear path back
2. Use standard navigation bars and titles
3. Flatten your information hierarchy - reduce depth
4. Make the current location obvious
5. Use tab bars for top-level categories, not related features

---

## Modality

### When to Use Modality
- Self-contained tasks (compose, create, edit)
- Critical information requiring acknowledgment
- Tasks that should not be interrupted

### Modal Presentation Types

| Type | Use For |
|------|---------|
| Sheet | Multi-step tasks, forms, content creation |
| Full-screen cover | Immersive content, complex flows |
| Alert | Critical decisions, destructive confirmations |
| Confirmation dialog | Multiple action choices |
| Popover | iPad contextual content |

```swift
// Sheet with detents
.sheet(isPresented: $showEditor) {
    EditorView()
        .presentationDetents([.medium, .large])
        .presentationDragIndicator(.visible)
}

// Alert for destructive action
.alert("Delete Item?", isPresented: $confirmDelete) {
    Button("Delete", role: .destructive) { delete() }
    Button("Cancel", role: .cancel) { }
} message: {
    Text("This cannot be undone.")
}

// Confirmation dialog for choices
.confirmationDialog("Share", isPresented: $showShare) {
    Button("Copy Link") { }
    Button("Share via Messages") { }
    Button("Cancel", role: .cancel) { }
}
```

### Modal Rules
1. Always provide a clear way to dismiss (Cancel/Done/Close)
2. Use `.presentationDragIndicator(.visible)` for sheets
3. Save button should be disabled until valid input exists
4. Warn before discarding unsaved changes
5. Keep modals focused on one task

---

## Data Entry & Forms

### Form Design
- Group related fields in sections
- Use appropriate input types (keyboard, picker, toggle)
- Provide default values when possible
- Validate inline, not just on submit

```swift
Form {
    Section("Personal Information") {
        TextField("Full Name", text: $name)
            .textContentType(.name)
        TextField("Email", text: $email)
            .textContentType(.emailAddress)
            .keyboardType(.emailAddress)
            .textInputAutocapitalization(.never)
    }

    Section("Preferences") {
        Picker("Category", selection: $category) {
            ForEach(categories) { Text($0.name).tag($0) }
        }
        Toggle("Enable Notifications", isOn: $notifications)
        DatePicker("Reminder", selection: $date)
    }
}
```

### Text Input Guidelines
- Set `.textContentType()` for autofill support
- Set `.keyboardType()` matching expected input
- Set `.textInputAutocapitalization()` appropriately
- Set `.autocorrectionDisabled()` for names, codes, emails
- Use `@FocusState` to manage focus flow

### Picker Guidelines
- Use inline pickers for 2-5 options
- Use navigation pickers for 6+ options
- Use segmented pickers for 2-4 mutually exclusive options with short labels
- Date pickers: use `.graphical` for date selection, `.wheel` for time

---

## Search

### Search Implementation
- Use `.searchable()` modifier
- Provide search suggestions
- Show recent searches
- Support search scopes for filtering

```swift
NavigationStack {
    List(filteredItems) { item in
        ItemRow(item: item)
    }
    .searchable(text: $searchText, prompt: "Search items")
    .searchSuggestions {
        ForEach(suggestions) { suggestion in
            Text(suggestion.name)
                .searchCompletion(suggestion.name)
        }
    }
    .searchScopes($scope) {
        Text("All").tag(SearchScope.all)
        Text("Recent").tag(SearchScope.recent)
        Text("Favorites").tag(SearchScope.favorites)
    }
}
```

### Search Principles
1. Place search prominently if it's a primary function
2. Show results as user types (progressive filtering)
3. Highlight matching text in results
4. Preserve search context when navigating results
5. Allow clearing search with one action

---

## Feedback & Status

### Loading States
- Always indicate loading activity
- Use `ProgressView` for indeterminate loading
- Use `ProgressView(value:)` for determinate progress
- Prefer skeleton screens over spinners for content loading

```swift
// Indeterminate
ProgressView("Loading...")

// Determinate
ProgressView(value: progress, total: 1.0) {
    Text("Downloading")
} currentValueLabel: {
    Text("\(Int(progress * 100))%")
}
```

### Empty States
- Provide helpful empty state with call to action
- Use `ContentUnavailableView` (iOS 17+)

```swift
ContentUnavailableView {
    Label("No Notes", systemImage: "note.text")
} description: {
    Text("Your notes will appear here.")
} actions: {
    Button("Create Note") { createNote() }
}
```

### Error States
- Clear, human-readable error messages
- Avoid technical jargon
- Provide actionable recovery (retry, contact support)
- Don't blame the user

```swift
ContentUnavailableView {
    Label("Connection Issue", systemImage: "wifi.slash")
} description: {
    Text("Check your internet connection and try again.")
} actions: {
    Button("Retry") { reload() }
}
```

### Haptic Feedback
- Use for confirmations, selections, and errors
- Match feedback intensity to action significance
- Never overuse - haptics lose meaning when constant

```swift
// Selection changed
UISelectionFeedbackGenerator().selectionChanged()

// Success
UINotificationFeedbackGenerator().notificationOccurred(.success)

// Error
UINotificationFeedbackGenerator().notificationOccurred(.error)

// Impact (button press)
UIImpactFeedbackGenerator(style: .medium).impactOccurred()
```

---

## Onboarding

### Onboarding Principles
1. Get users into the app quickly - minimize onboarding
2. Show value before asking for anything (permissions, sign-up)
3. Defer sign-in until it's needed for a feature
4. Request permissions in context, not upfront
5. Make onboarding skippable

### Permission Requests
- Request only when the feature is about to be used
- Explain WHY before the system prompt appears
- Gracefully handle denial - provide alternative paths

```swift
// Pre-permission explanation
.alert("Enable Notifications?", isPresented: $showPermissionExplainer) {
    Button("Enable") { requestNotificationPermission() }
    Button("Not Now", role: .cancel) { }
} message: {
    Text("Get reminders for upcoming events and important updates.")
}
```

---

## Managing Content

### Drag and Drop
- Support for reordering lists
- Cross-app drag and drop on iPad/Mac
- Visual feedback during drag

### Undo/Redo
- Support undo for destructive or significant changes
- Use system undo gesture (shake on iOS, Cmd+Z on Mac)
- Consider undo snackbars for immediate feedback

### Delete Patterns
- Swipe to delete for lists
- Require confirmation for destructive deletes
- Provide undo when possible instead of confirmation

```swift
// Swipe to delete
.onDelete { indexSet in
    items.remove(atOffsets: indexSet)
}

// OR confirmation for permanent delete
.swipeActions(edge: .trailing, allowsFullSwipe: false) {
    Button("Delete", role: .destructive) {
        confirmDelete = true
    }
}
```

---

## Offering Help

### In-App Help
- Use tooltips and inline hints over separate help screens
- Progressive disclosure - show advanced features gradually
- Use `.popoverTip()` (iOS 17+) for contextual tips

```swift
// TipKit for contextual help
struct FavoriteTip: Tip {
    var title: Text { Text("Add to Favorites") }
    var message: Text? { Text("Tap the heart to save items for later.") }
    var image: Image? { Image(systemName: "heart") }
}

Button(action: favorite) {
    Image(systemName: "heart")
}
.popoverTip(FavoriteTip())
```

### Help Principles
1. Design the UI to be self-explanatory first
2. Use contextual help near the relevant feature
3. Keep help text concise and actionable
4. Don't rely on help to fix confusing UI - fix the UI
