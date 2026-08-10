# Contributing

Thanks for contributing to Polaris Remote.

## Before You Start

Please read:

- `README.md`
- `ARCHITECTURE.md`
- `ROADMAP.md`
- `docs/PROJECT_PRINCIPLES.md`

## Development Expectations

- Keep changes focused.
- Prefer simple solutions over premature abstraction.
- Do not couple UI code directly to television-specific protocol code.
- Add tests for protocol parsing, command mapping, and important state logic where practical.
- Avoid adding dependencies without a clear reason.
- Do not introduce tracking, advertising, or cloud services without explicit project-level discussion.
- Never commit API keys, credentials, pairing secrets, signing files, or other sensitive material.

## Branches

Use short descriptive branch names, for example:

```text
feature/vidaa-discovery
feature/remote-ui
fix/reconnect-timeout
```

## Commits

Prefer small, descriptive commits. Suggested format:

```text
feat: add manual TV connection
fix: handle connection timeout
docs: update protocol support notes
test: add Roku command mapping tests
refactor: isolate discovery service
```

## Pull Requests

A pull request should explain:

1. What changed.
2. Why the change is needed.
3. How it was tested.
4. Which television platform/model was used for protocol changes, when applicable.
5. Any new Android permissions or dependencies introduced.

Protocol support claims should include enough testing information to reproduce the result.

## Protocol Contributions

When adding or changing a TV protocol:

- document the transport and discovery mechanism
- document whether pairing/authentication is required
- avoid undocumented assumptions about all Hisense models
- handle unsupported commands explicitly
- ensure network resources are closed correctly
- do not disable TLS verification as a shortcut in production code
- update `docs/PROTOCOL_SUPPORT.md`

## Code Style

Follow Kotlin and Android conventions. Use automatic formatting where available. Names should describe intent rather than implementation trivia.

## Issues

Bug reports are most helpful when they include:

- Hisense model number
- TV operating system/platform
- Android device and Android version
- app version or commit
- steps to reproduce
- expected behavior
- actual behavior

Do not post passwords, Wi-Fi credentials, pairing secrets, private IP information you do not wish to share, or other sensitive data.

## License

By contributing to Polaris Remote, you agree that your contributions are submitted under the repository's Apache License 2.0 unless explicitly stated otherwise.
