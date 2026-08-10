# Polaris Remote

Polaris Remote is a free, open-source Android remote-control app focused on Hisense televisions.

The goal is simple: provide a clean, reliable remote without subscriptions, accounts, or invasive tracking.

## Project Status

**Phase:** Architecture and project foundation

The first development milestone is to connect to a supported Hisense TV on the same local network and send basic remote commands.

## Planned Features

- TV discovery on the local network
- Manual IP connection fallback
- Pairing and saved devices
- Power controls where supported by the TV platform
- Volume up/down and mute
- Directional navigation and OK/select
- Home and back
- Input/source selection
- Channel controls
- Playback controls
- Numeric keypad
- Haptic feedback
- Dark mode
- Multiple saved televisions

Future possibilities include Android widgets, Quick Settings controls, custom layouts, text entry, favorite apps, and Wear OS support.

## Supported TV Platforms

Hisense televisions use several operating systems depending on model and region. Polaris Remote is designed around protocol adapters so each platform can be implemented independently.

Initial targets:

- Hisense VIDAA
- Hisense Roku TV
- Hisense Android TV / Google TV

Support will be added only after the protocol can be implemented and tested reliably.

## Technology

- **Language:** Kotlin
- **UI:** Jetpack Compose
- **Architecture:** MVVM with repository/service boundaries
- **Networking:** Android networking APIs with OkHttp or Ktor where appropriate
- **Discovery:** SSDP, mDNS, or platform-specific discovery mechanisms
- **Storage:** Android DataStore or Room depending on persistence needs
- **Build:** Gradle

## Core Principles

1. Free core remote functionality.
2. No account required for normal local remote use.
3. No unnecessary collection of user data.
4. Local-network control whenever possible.
5. Clear separation between UI and television protocols.
6. Small, testable development increments.
7. Every supported protocol must fail safely and clearly.

See [docs/PROJECT_PRINCIPLES.md](docs/PROJECT_PRINCIPLES.md) for the full project principles.

## Architecture

The UI interacts with a common remote interface rather than individual television protocols. Platform adapters translate common commands into the protocol required by the connected television.

```text
UI
 |
ViewModel
 |
Remote Repository
 |
Remote Controller Interface
 |-------------------------------|
VIDAA Adapter   Roku Adapter   Android/Google TV Adapter
```

See [ARCHITECTURE.md](ARCHITECTURE.md) for details.

## Development Roadmap

Development begins with the smallest useful milestone: manually connect to one supported television and make it respond to a small set of commands. Automatic discovery and broader platform support come afterward.

See [ROADMAP.md](ROADMAP.md).

## Contributing

Contributions are welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) before opening a pull request.

## Trademark Notice

Hisense, Roku, Android, Google TV, VIDAA, and other referenced product names are trademarks of their respective owners. Polaris Remote is an independent open-source project and is not affiliated with or endorsed by Hisense or those platform owners.

## License

Licensed under the [Apache License 2.0](LICENSE).
