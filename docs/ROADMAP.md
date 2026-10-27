# HabitTracker — Development Roadmap

## Project Goal

Build a native Android habit-tracking application using Kotlin and Jetpack Compose.

The application will help users create daily habits, mark them as completed, and eventually track their consistency through streaks and statistics.

This project is also an opportunity to learn modern Android development, Kotlin, and maintainable software architecture.

## Phase 1 — Project Foundation

- [x] Create Android Studio project
- [x] Initialize Git
- [x] Push project to GitHub
- [x] Create documentation files
- [ ] Establish application package structure
- [ ] Create the first Compose screen
- [ ] Run the application in an Android emulator

## Phase 2 — Habit List (MVP)

- [ ] Define a Habit model
- [ ] Display a list of sample habits
- [ ] Build a reusable HabitItem component
- [ ] Mark habits as complete or incomplete
- [ ] Introduce a ViewModel and observable UI state
- [ ] Add basic unit tests

## Phase 3 — Habit Management

- [ ] Create new habits
- [ ] Edit existing habits
- [ ] Delete habits
- [ ] Validate user input

## Phase 4 — Local Persistence

- [ ] Introduce Room database
- [ ] Implement a HabitRepository
- [ ] Persist habits between app launches
- [ ] Connect persistence to the ViewModel

## Phase 5 — Streaks and Progress

- [ ] Track daily completion history
- [ ] Calculate current and longest streaks
- [ ] Display habit progress
- [ ] Add basic statistics

## Phase 6 — Polish

- [ ] Improve accessibility
- [ ] Add loading, empty, and error states
- [ ] Support light and dark themes
- [ ] Expand automated tests
- [ ] Prepare a release build

## Development Principles

- Build features incrementally.
- Keep the application runnable after each milestone.
- Understand new concepts before introducing additional complexity.
- Write maintainable, testable code.
- Commit meaningful changes to Git regularly.