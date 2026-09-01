# Swift Best Practices

 Practical guide to programming projects with Swift.

Starting this project, I went looking for references and found that the Swift community already has excellent, authoritative guides. Rather than write a new one from scratch, this repo curates the best of them, adds a recommended Xcode project structure, and keeps everything in one place.

Keep watching this space. More to come.

---

## References

| Guide | Source |
|---|---|
| [Swift API Design Guidelines](https://www.swift.org/documentation/api-design-guidelines/) | Apple / Swift.org |
| [Google Swift Style Guide](https://google.github.io/swift/) | Google |
| [GitHub Swift Style Guide](https://github.com/github/swift-style-guide) | GitHub |
| [Kodeco Swift Style Guide](https://github.com/kodecocodes/swift-style-guide) | Kodeco |

### Linting & Formatting Tools

| Tool | Purpose |
|---|---|
| [SwiftLint](https://github.com/realm/SwiftLint) | Linting — community-owned, enforce style at build time |
| [swift-format](https://github.com/swiftlang/swift-format) | Auto-formatting — Apple's own |
| [SwiftLintPlugins](https://github.com/SimplyDanny/SwiftLintPlugins) | SPM plug-ins for SwiftLint integration |

---

## Xcode Project Organisation

Recommended folder structure (hat tip to Claude for the suggestion — it holds up well):

```
MyApp/
├── App/
│   ├── MyAppApp.swift       # @main entry point
│   └── AppDelegate.swift    # if needed
├── Features/                # or "Screens" or "Modules"
│   ├── Home/
│   │   ├── HomeView.swift
│   │   └── HomeViewModel.swift
│   ├── Profile/
│   │   ├── ProfileView.swift
│   │   └── ProfileViewModel.swift
│   └── Settings/
│       └── SettingsView.swift
├── Core/                    # shared business logic
│   ├── Models/
│   ├── Services/
│   └── Repositories/
├── UI/                      # reusable UI components
│   ├── Components/
│   └── Styles/
├── Utilities/               # extensions, helpers
└── Resources/               # assets, localisation, etc.
```

### Key Principles

* Organise by feature, not by type.** Grouping `HomeView`, `HomeViewModel`, and `HomeService` together beats a flat `ViewModels/` folder with 30 files in it. Feature-based organisation scales much better.
* Keep the navigator clean.** The file navigator is your daily workspace — if it takes more than 2–3 clicks to find something, the structure needs simplifying.
* Match your filesystem.** With real folders, what you see in Finder matches what you see in Xcode. This makes Git diffs, PR reviews, and onboarding new devs significantly easier.
* Use Swift Package Manager for true modularity.** If your app grows large, extracting features into local Swift packages (`File → New → Package`) gives you proper module boundaries, faster compile times, and enforced separation of concerns — better than folder organisation alone.
