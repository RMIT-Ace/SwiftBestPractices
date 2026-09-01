# SwiftBestPractices
Practical guide to programming projects with Swift

Mention here that I was starting working on this project and look around for references and found that there are good recommendations everywhere - no need to write up new one.

# References

1. https://www.swift.org/documentation/api-design-guidelines/
2. ⭐️⭐️⭐️ https://google.github.io/swift/
3. Managing files and folders in your Xcode project
4. https://github.com/github/swift-style-guide
5. https://github.com/kodecocodes/swift-style-guide
6. Linting
    1. For linting 👉 https://github.com/realm/SwiftLint (open source community own)
    2. For auto-formatting 👉 https://github.com/swiftlang/swift-format (Apple’s own)
    3. Plug-ins: https://github.com/SimplyDanny/SwiftLintPlugins


# Xcode Project Organisation
Recommended Folder Structure (mention that this was recommended by Claude - which I think I can agree upon)

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

## Key Principles
- Organise by feature, not by type. Grouping HomeView, HomeViewModel, and HomeService together beats having a flat ViewModels/ folder with 30 files in it. Feature-based organisation scales much better.

- Keep the navigator clean. The file navigator is your daily workspace — if it takes more than 2–3 clicks to find something, the structure needs simplifying.

- Match your filesystem. With real folders, what you see in Finder matches what you see in Xcode. This makes Git diffs, PR reviews, and onboarding new devs significantly easier.

- Use Swift Package Manager for true modularity. If your app grows large, extracting features into local Swift packages (via File → New → Package) gives you proper module boundaries, faster compile times, and enforced separation of concerns — better than just folder organisation alone.
