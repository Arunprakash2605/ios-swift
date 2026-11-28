# PetCare – Pet Care & Vaccination Tracker (iOS)

A multi-screen SwiftUI + SwiftData iOS application built with strict **MVVM architecture** for managing pets, vaccinations, veterinary visits, grooming, and diet plans.

## Project Location & Structure

All source files, assets, configuration files, and Xcode project files live inside the `PetCare` folder:

- `App/` — `PetCareApp.swift`, `AppState.swift`
- `Models/` — `Pet.swift`, `CareEntry.swift`, `CareCategory.swift`, `User.swift`
- `ViewModels/` — `AuthenticationViewModel.swift`, `DashboardViewModel.swift`, `PetViewModel.swift`, `CareViewModel.swift`, `SearchViewModel.swift`
- `Views/` — `Authentication/`, `Dashboard/`, `Pets/`, `Care/`, `Search/`, `Profile/`, `Components/`, `MainTabView.swift`
- `Services/` — `BiometricService.swift`, `StorageService.swift`, `NotificationService.swift`
- `Utilities/` — `AppColors.swift`, `AppConstants.swift`, `DateExtensions.swift`
- `Resources/Assets.xcassets` — AppIcon, PetCareLogo, AccentColor, and lightweight pet thumbnails
- `Info.plist` — Face ID usage description and iPhone Portrait-only orientation config
- `PetCare.xcodeproj` & `project.yml` — Xcode project targeting iOS 17.0+ (iPhone only)

## Features Implemented

- **Biometric & Manual Authentication**: Real `LocalAuthentication` (`LAContext`) Face ID / Touch ID availability checking and evaluation, plus validated email/password sign-in and local account registration.
  - Default seeded account for quick testing: `owner@petcare.app` / `PetCare123` (or tap **Fill Default Account** on the Sign In screen, or create a new local account).
- **Dashboard**: Personalized greeting, current date, notification reminder summary, 4 live metric cards (*Total Pets*, *Upcoming*, *Due Vaccines*, *Completed Care*), quick actions, upcoming appointments, and recent care activities.
- **Pet Management**: Add, view, edit, search, and delete pets (`Dog`, `Cat`, `Bird`, `Rabbit`, `Other`) with `PhotosPicker` support and lightweight asset thumbnails.
- **Care & Vaccination Records**: Scrollable list, add/detail/edit/delete flows with confirmation alerts, and one-tap *Mark as Completed*.
- **Search & Filtering**: Dynamic search by activity title or pet name, category filters (`All`, `Vaccination`, `Vet Visit`, `Grooming`, `Diet`), status filters (`All Status`, `Scheduled`, `Completed`, `Overdue`), and *Clear Filter*.
- **Automatic Status Tracking**: Evaluates `Scheduled` (today or future) vs `Overdue` (past date) on launch, foreground resume, and data updates without overwriting `Completed`.
- **Local Notifications**: `UserNotifications` permission handling, duplicate-free reminder scheduling, and automatic cancellation on delete or completion.
- **Profile & Bottom Navigation**: Custom 4-tab bottom bar (*Home*, *My Pets*, *Care Records*, *Profile*) with biometric, notification, and logout controls.

## Opening & Running (Windows VS Code vs macOS Xcode)

- **Windows / VS Code**: You can browse, edit, and organize all Swift files, `Assets.xcassets`, `Info.plist`, and `project.yml` directly inside the `PetCare` folder.
- **macOS & Xcode (Required for Native iOS Build & Simulator)**:
  1. Transfer or unzip `PetCare_Project.zip` on a Mac with **Xcode 15.0+** (iOS 17.0 SDK or newer).
  2. Open `PetCare/PetCare.xcodeproj` directly in Xcode (or run `xcodegen generate` inside `PetCare/` using `project.yml`).
  3. Select an **iPhone** simulator (configured for **iPhone only** and **Portrait orientation only**).
  4. Build and run (`Cmd + R`).
  5. To test Face ID in the iOS Simulator, choose **Features → Face ID → Enrolled**, then test **Matching Face** and **Non-matching Face**.
