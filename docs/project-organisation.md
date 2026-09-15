# Flat Structure

Best for: solo projects, prototypes, experiments, small projects.

```
MyApp/
├── MyAppApp.swift
├── ContentView.swift
├── HomeView.swift
├── ProfileView.swift
├── UserModel.swift
├── NetworkService.swift
└── Assets.xcassets
```

# Type-Based Structure

Best for: small-to-medium, MVC/MVVM

```
MyApp/
├── Models/
│   └── User.swift
├── Views/
│   ├── HomeView.swift
│   └── ProfileView.swift
├── ViewModels/
│   ├── HomeViewModel.swift
│   └── ProfileViewModel.swift
├── Services/
│   └── NetworkService.swift
└── Resources/
```

# Feature-Based Structure

Best for: medium-to-large projects.

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

* Organise by feature, not by type.** Grouping `HomeView`, `HomeViewModel`, and `HomeService` together beats a flat `ViewModels/` folder with 30 files in it. Feature-based organisation scales much better.
* Keep the navigator clean.** The file navigator is your daily workspace — if it takes more than 2–3 clicks to find something, the structure needs simplifying.
* Match your filesystem.** With real folders, what you see in Finder matches what you see in Xcode. This makes Git diffs, PR reviews, and onboarding new devs significantly easier.
* Use Swift Package Manager for true modularity.** If your app grows large, extracting features into local Swift packages (`File → New → Package`) gives you proper module boundaries, faster compile times, and enforced separation of concerns — better than folder organisation alone.

# MVVM-C (with Coordinators)

Best for: apps with complex navigation flows.

```
MyApp/
├── App/
│   └── AppCoordinator.swift
├── Features/
│   ├── Home/
│   │   ├── HomeCoordinator.swift
│   │   ├── HomeView.swift
│   │   └── HomeViewModel.swift
│   └── Profile/
│       ├── ProfileCoordinator.swift
│       ├── ProfileView.swift
│       └── ProfileViewModel.swift
├── Core/
│   ├── Navigation/
│   └── Services/
└── Resources/
```
