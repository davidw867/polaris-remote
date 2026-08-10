# Development Guide

## Prerequisites

Recommended local tools:

- Android Studio (current stable release)
- Android SDK
- JDK version required by the selected Android Gradle Plugin
- Git
- A physical Android device for testing
- A supported Hisense television on the same local network for protocol testing

The exact Android SDK, Gradle, Kotlin, and dependency versions will be pinned when the Android project is created.

## Initial Android Project

The planned application stack is:

- Kotlin
- Jetpack Compose
- Material 3
- Coroutines and Flow
- MVVM
- repository/service boundaries
- AndroidX lifecycle components

Networking libraries should be selected based on protocol needs rather than added preemptively.

## Package Layout

See `ARCHITECTURE.md` for the intended package structure.

The first implementation should remain small. Empty layers or abstractions should not be created only to match the diagram.

## Local Testing

Protocol testing should use a physical television whenever possible.

Recommended test flow:

1. Put the Android device and television on the same trusted local network.
2. Confirm the TV has network remote/control functionality enabled when required.
3. Start with manual IP connection.
4. Verify one command at a time.
5. Record the model, platform, and behavior in protocol documentation.
6. Test disconnect, reconnect, TV-offline, and Wi-Fi-loss scenarios.

## Logging

Development logs should contain enough information to debug connection state without leaking secrets.

Do not log:

- pairing secrets
- authentication tokens
- Wi-Fi passwords
- private user data

Protocol packet logging should be sanitized before it is enabled in production builds.

## Android Permissions

Every Android permission must have a specific documented purpose. Network discovery requirements may vary by Android version, so permission behavior must be tested against the project's supported Android API levels.

Do not request broad permissions simply to avoid implementing modern Android permission handling correctly.

## Dependencies

Before adding a dependency, consider:

- Is it needed for the current milestone?
- Is it actively maintained?
- What license does it use?
- Does it increase app size substantially?
- Does it collect telemetry?
- Can Android/Kotlin standard libraries solve the problem cleanly?

Keep the dependency surface small.

## Definition of Done

A feature is considered complete when:

- it works for its documented use case
- errors are handled without crashing
- relevant tests pass
- architecture boundaries remain intact
- documentation is updated when behavior or support changes
- no secrets or test credentials are committed

Protocol features additionally require documented hardware/platform testing before being described as supported.

## Versioning

The project will use semantic-style versioning for releases once release builds begin.

Early development may use `0.x` versions while protocol and UI behavior are still evolving.
