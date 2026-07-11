# Results

This section covers the system analysis, design, and development outcomes, followed by the testing and validation results.

## System Analysis

Unified Modelling Language (UML) tools were used to represent the information gathered during the study phase, ensuring system logic aligned with real-world fraud experiences identified among Kampala users.

**Use case groupings** (primary actor: the mobile money user):

- **Application Launch:** launching the app, splash/loading screens, navigating to home.
- **Scam Simulation:** starting a simulation, listening to voice-guided scenarios, choosing an action (Send Money, Ignore, or Report), receiving feedback.
- **Settings:** changing language, adjusting audio volume, enabling offline mode, exporting/importing progress.
- **Learning:** viewing learning milestones and watching scam-awareness videos.

**Typical simulation session flow:** launch app → tap "Start Simulation" → system plays a voice-guided scenario → user chooses a response → system shows feedback (safe/risky) → system updates and stores progress locally.

**Data flow (Level 0):** data moves between the user, the app's simulation engine, the local SQLite database, and the optional cloud backup service — covering scenario data, user decisions, and progress information.

### Functional Requirements

| ID | Requirement |
|---|---|
| FR1 | Present pre-recorded, voice-guided scam scenarios in English or Luganda. |
| FR2 | Allow the user to choose an action in response to a scenario (Send Money, Ignore, or Report). |
| FR3 | Record the user's decision and provide immediate feedback on whether it was safe or risky. |
| FR4 | Track and display the user's progress and learning milestones across sessions. |
| FR5 | Allow the user to change language, audio, and accessibility settings. |
| FR6 | Play short educational videos related to common mobile money scams. |
| FR7 | Allow the user to export or back up progress data for future cloud synchronisation. |
| FR8 | Function fully without an active internet connection. |

### Non-Functional Requirements

| ID | Requirement |
|---|---|
| NFR1 | **Usability** — simple enough for users with limited digital literacy to navigate without assistance. |
| NFR2 | **Performance** — scenario audio and screen transitions load within two seconds on a mid-range Android device. |
| NFR3 | **Availability** — core simulation features remain available offline once installed. |
| NFR4 | **Portability** — runs on Android OS 8.0+, codebase structured for future iOS/web ports. |
| NFR5 | **Data privacy** — locally stored progress is not transmitted without explicit user consent. |
| NFR6 | **Maintainability** — modular Flutter architecture allows new scam scenarios with minimal code changes. |

## System Design

**Architecture (four layers):**

1. **Presentation Layer** — Flutter widgets and screens.
2. **Application/Logic Layer** — Dart classes controlling scenario flow, decision evaluation, and progress calculation.
3. **Local Data Layer** — SQLite database accessed via `sqflite`.
4. **Cloud Layer** — optional Firebase-based backup and future analytics.

**Database design** — four principal SQLite tables:

| Table | Purpose |
|---|---|
| **Users** | Local device profile, preferred language, accessibility settings |
| **Scenarios** | Scenario identifiers, script text, audio file references, difficulty levels |
| **Decisions** | Each attempt: action chosen and whether it was safe or risky |
| **Progress** | Aggregated completed scenarios, scores, and milestones |

**Navigation design:** centered on a home screen, branching into Scam Simulation, Watch Videos, View Progress, and Settings — every module returns to home on completion, prioritizing predictability for users with limited digital literacy.

## System Development

- **Engineering stack:** Flutter SDK, Dart; Visual Studio Code and Android Studio as IDEs; GitHub for version control.
- **Key dependencies:** `sqflite` (offline SQLite storage), `just_audio` / `audioplayers` (concurrent low-latency English/Luganda playback), `path_provider` (cached resources and local voice scripts).

**Screens implemented:**

- **Home screen** — CyberScam Lab logo and a prominent "Start Simulation" button.
- **Scam Simulation screen** — plays an audio scenario while displaying script text, with three colored response buttons (Send Money, Ignore, Report).
- **Feedback screen** — explains whether the chosen action was safe or risky.
- **Progress screen** — aggregates completed scenarios and learning milestones.
- **Settings screen** — toggle English/Luganda, adjust volume, manage offline mode.

## Testing and Validation

Testing combined **formative** evaluation (during development) and **summative** evaluation (structured sessions with students, market vendors, and boda-boda riders in Kampala), run on three Android test devices of varying specification.

### Test Data Matrix and Results

| Test Case | Input Test Data | Expected Result | Actual Result |
|---|---|---|---|
| TC01 | User selects a scam scenario and listens to the voice guide | Scenario plays correctly with synchronised voice guidance | **Passed** — audio and on-screen text stayed synchronised on all three devices |
| TC02 | User makes a decision during a simulation | System records the choice and provides immediate feedback | **Passed** — feedback displayed within under one second |
| TC03 | User completes multiple scenarios | Progress is tracked and displayed accurately | **Passed** — progress screen reflected completed scenarios and scores correctly |
| TC04 | User changes language to Luganda | All voice prompts and labels switch to Luganda | **Passed** — audio and labels switched; two minor untranslated strings were corrected |
| TC05 | User accesses the app without internet connection | Offline access works; scenarios and audio load from local storage | **Passed** — all core modules functioned normally in airplane mode |
| TC06 | User submits feedback after a simulation | Feedback is saved locally or sent to the cloud if connected | **Passed** — feedback saved locally and synced on next connection |
| TC07 | User navigates between modules | Navigation is smooth and all buttons respond as expected | **Passed** — no crashes across 30 navigation cycles |

**Summary:** All seven test cases passed. Two untranslated interface strings in the Luganda language pack were found and fixed before the final build.

### Usability Evaluation (Simplified SUS, n = 15)

| SUS Statement | Average Score (out of 5) |
|---|---|
| I found the app easy to use. | 4.4 |
| I would recommend this app to a friend or family member. | 4.6 |
| The voice guidance made the scenarios easier to understand. | 4.5 |
| I felt confident I could tell a safe action from a risky one after using the app. | 4.2 |
| I could use the app without needing help from someone else. | 4.1 |

**Interpretation:** Users generally found CyberScam Lab easy to use and reported increased confidence in distinguishing safe actions from risky ones when facing a mobile money scam. The lowest-scoring statement (independent use, 4.1) motivated the "User Onboarding" recommendation in [`conclusion.md`](conclusion.md).
