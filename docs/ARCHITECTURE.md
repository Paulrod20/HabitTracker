# HabitTracker — Architecture

## Overview

HabitTracker is a native Android application built using Kotlin and Jetpack Compose.

The project follows a lightweight, feature-first architecture using the Model–View–ViewModel (MVVM) pattern.

Our primary goal is to separate presentation, application state, business rules, and data access.

## Architecture Layers

### 1. UI Layer — Jetpack Compose

Responsibilities:

- Display data provided by the presentation layer.
- Render loading, empty, and error states.
- Forward user interactions through callbacks.
- Manage local visual state when appropriate.

The UI should NOT:

- Access the database directly.
- Perform persistence operations.
- Implement business rules such as streak calculations.
- Own application-wide business state.

Where practical, screen composables will receive immutable UI state and callbacks rather than directly depending on a ViewModel.

### 2. ViewModel Layer

Responsibilities:

- Manage screen-level state.
- Respond to user actions.
- Coordinate operations with repositories or business logic.
- Expose observable state to the UI.

ViewModels should not depend on Android Views or contain composable UI code.

### 3. Domain / Business Logic

Responsibilities:

- Represent application rules.
- Calculate streaks and completion statistics.
- Validate habit-related operations.

Business logic should be testable independently of the UI.

A separate domain package will be introduced when the complexity justifies it.

### 4. Data Layer

Responsibilities:

- Read and write habit data.
- Abstract persistence behind repositories.
- Map stored data into application models when necessary.

Room will be introduced when local persistence becomes part of the application.

## Proposed Package Structure

```text
com.example.habittracker/
├── MainActivity.kt
├── core/
│   └── ui/
├── feature/
│   └── habits/
│       ├── model/
│       ├── ui/
│       └── HabitsViewModel.kt
├── data/
└── navigation/
```

Packages will be created incrementally as needed.

## State Management

- ViewModels will expose screen state using StateFlow.
- Compose will observe state and recompose when relevant values change.
- UI events will be communicated through callbacks.
- State will flow downward; events will flow upward.
- State models will favor immutability.

## Testing Strategy

- Unit-test business logic and ViewModels.
- Test repository behavior when persistence is introduced.
- Use Compose UI tests for important user interactions.
- Keep presentation composables independently previewable where practical.

## Architectural Principles

1. **Separation of concerns:** Each layer has a clear responsibility.
2. **Single source of truth:** Avoid duplicating authoritative application state.
3. **Unidirectional data flow:** State moves toward the UI; events move toward the state owner.
4. **Testability:** Business rules should not require an Android emulator to test.
5. **Simplicity:** Avoid abstractions until they solve a real problem.
6. **Maintainability:** Prefer readable, consistent code over unnecessary cleverness.

## Architecture Decisions

Architecture decisions will be updated as the project grows.

Initial decisions:

- Language: Kotlin
- UI framework: Jetpack Compose with Material 3
- Presentation pattern: MVVM
- Project organization: Feature-first
- Asynchronous state: Kotlin Coroutines and StateFlow
- Planned local persistence: Room
- Dependency injection: Deferred until needed

## Native Android Experience

HabitTracker should embrace Android platform conventions and capabilities.

- Use edge-to-edge layouts with appropriate window inset handling.
- Support transparent or translucent system bars and subtle gradient scrims where appropriate.
- Ensure content remains readable behind the status bar.
- Respect Android gesture navigation and system back behavior.
- Support dynamic color (Material You) on compatible devices.
- Support light and dark themes.
- Use native Android animations, haptics, and system integrations when they improve the experience.
- Respect accessibility settings, font scaling, and reduced-motion preferences where supported.
- Prefer Android-native interaction patterns over copying iOS behavior directly.

The goal is to deliver a polished, platform-native experience while borrowing good visual design ideas from other platforms.