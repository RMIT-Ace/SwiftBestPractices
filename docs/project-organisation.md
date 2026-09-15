# Well-Known Project Organisations

* [Flat Structure](#flat-structure)
* [Type-Based Structure](#type-based-structure)
* [Feature-Based Structure](#feature-based-structure)
* [MVVM-C](#mvvm-c-with-coordinators)
* [TCA - The Composible Architecture](#tca---the-composable-architecture)
* [SPM Modular](#spm-modular-swift-package-management)

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

# TCA - The Composable Architecture

Best for: Strict unidirectional data flow.

```
MyApp/
├── App/
│   ├── AppFeature.swift       # Root reducer
│   └── AppView.swift
├── Features/
│   ├── Home/
│   │   ├── HomeFeature.swift  # Reducer + State + Action
│   │   └── HomeView.swift
│   └── Profile/
│       ├── ProfileFeature.swift
│       └── ProfileView.swift
├── Dependencies/              # TCA dependency clients
└── Resources/
```

# SPM Modular (Swift Package Management)

Best for: writing (swift) packages.

```
MyApp/                          # Xcode app target (thin shell)
Packages/
├── AppFeature/                 # Root feature package
├── HomeFeature/
├── ProfileFeature/
├── CoreUI/                     # Shared design system
├── Networking/
└── Models/
```

Each feature is a separate local Swift package with its own Package.swift. The app target just composes them. This is the pattern used by large teams (and by Apple internally). Gives you compile-time module boundaries and significantly faster incremental builds. 

Reference: [Apple's Organizing your code with local packages](https://developer.apple.com/documentation/xcode/organizing-your-code-with-local-packages)
