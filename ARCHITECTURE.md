# Architecture

Polaris Remote uses a layered Android architecture designed to keep television-specific protocol logic isolated from the user interface.

## Goals

- Keep the app easy to understand and maintain.
- Allow new Hisense platforms to be added without rewriting the UI.
- Make networking and protocol code independently testable.
- Avoid unnecessary abstractions until they provide clear value.
- Keep Android framework dependencies near the edges of the system where practical.

## High-Level Flow

```text
Jetpack Compose UI
        |
     ViewModel
        |
   Use Cases / Actions
        |
 RemoteRepository
        |
 RemoteController
        |
+-------------------------------+
| VIDAA | Roku | Android/Google |
+-------------------------------+
        |
 Local network / TV
```

## Suggested Package Structure

```text
app/src/main/java/.../polarisremote/
├── app/
│   └── App.kt
├── core/
│   ├── discovery/
│   ├── network/
│   ├── model/
│   └── util/
├── data/
│   ├── repository/
│   └── storage/
├── domain/
│   ├── model/
│   ├── repository/
│   └── usecase/
├── remote/
│   ├── RemoteController.kt
│   ├── vidaa/
│   ├── roku/
│   └── androidtv/
└── ui/
    ├── devices/
    ├── remote/
    ├── settings/
    └── theme/
```

This structure is a starting point, not a rigid rule. It should evolve only when the codebase demonstrates a real need.

## Core Abstraction

A common controller interface should represent actions the UI understands.

Conceptually:

```kotlin
interface RemoteController {
    suspend fun connect(device: TvDevice): Result<Unit>
    suspend fun disconnect()
    suspend fun send(command: RemoteCommand): Result<Unit>
    fun isConnected(): Boolean
}
```

`RemoteCommand` should model application-level actions such as volume up, home, back, navigation, playback, and input selection.

Each protocol adapter is responsible for translating those commands into platform-specific network traffic.

## Device Discovery

Discovery belongs outside the UI. A discovery service should expose discovered televisions as domain models.

Different platforms may use different mechanisms, including:

- SSDP / UPnP
- mDNS
- platform-specific broadcast or multicast discovery
- manual IP entry

The discovery layer should not assume that every Hisense TV uses the same protocol.

## Repository Layer

`RemoteRepository` coordinates:

- discovered and saved devices
- selecting the correct protocol adapter
- connection state
- pairing state
- sending commands
- translating low-level failures into user-facing error categories

The ViewModel should not open sockets or construct protocol packets directly.

## UI Layer

Jetpack Compose screens should primarily render state and emit user actions.

Expected screens include:

- Device selection/discovery
- Pairing/connect flow
- Main remote
- Numeric keypad / expanded controls
- Settings

UI state should be immutable where practical and owned by ViewModels.

## Storage

Use the smallest persistence tool that fits the requirement.

DataStore is appropriate for lightweight preferences and recently used device information. Room should only be introduced if structured local data grows enough to justify a database.

Never store credentials, pairing secrets, or sensitive tokens in plain text if a platform protocol requires them.

## Networking

Protocol adapters may use HTTP, WebSockets, TCP/TLS, UDP, MQTT, or other mechanisms depending on the TV platform.

Rules:

- use timeouts
- close connections cleanly
- handle network loss without crashing
- avoid blocking the main thread
- validate received data before using it
- do not transmit user data outside the local network unless a feature explicitly requires it and the user understands why

## Dependency Direction

Higher-level application logic must not depend on concrete protocol implementations.

Preferred direction:

```text
UI -> Domain <- Data / Protocol Implementations
```

Concrete adapters implement interfaces defined at a higher level.

## Testing Strategy

### Unit Tests

Test:

- command mapping
- state transitions
- protocol message construction/parsing
- repository selection logic
- error translation

### Integration Tests

Test protocol adapters against real televisions whenever possible.

### UI Tests

Focus on critical flows such as device selection, connection state, and command controls.

## Error Handling

Errors should be categorized into understandable states, for example:

- TV not found
- connection refused
- pairing required
- authentication failed
- command unsupported
- network unavailable
- connection timed out
- protocol error

Raw protocol exceptions should not be displayed directly to normal users.

## Security and Privacy

Polaris Remote is local-first. Protocol implementations should request only the Android permissions they genuinely need. Broad network or device permissions must be documented before introduction.

See `docs/PROJECT_PRINCIPLES.md` for the privacy and product rules that guide architecture decisions.
