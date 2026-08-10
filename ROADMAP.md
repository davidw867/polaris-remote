# Roadmap

Polaris Remote will be developed in small, testable milestones. The priority is a reliable remote before advanced features.

## Phase 0 — Project Foundation

- [x] Create repository
- [x] Add Apache License 2.0
- [x] Define architecture
- [x] Define project principles
- [x] Define contribution and development documentation
- [ ] Create Android Studio project
- [ ] Configure Gradle and package namespace
- [ ] Add baseline CI

## Phase 1 — First Working Remote

Goal: make a real supported Hisense television respond.

- [ ] Build basic Jetpack Compose remote screen
- [ ] Add manual IP address entry
- [ ] Implement one tested protocol adapter
- [ ] Connect/disconnect state handling
- [ ] Navigation: up/down/left/right/OK
- [ ] Home and back
- [ ] Volume up/down and mute
- [ ] Display clear connection errors

Exit criterion: commands work reliably against at least one physical Hisense TV.

## Phase 2 — Device Discovery and Pairing

- [ ] Automatic local-network discovery
- [ ] Identify TV platform where possible
- [ ] Pairing/authentication flow where required
- [ ] Save known televisions
- [ ] Reconnect to last-used television
- [ ] Manual connection remains available as fallback

## Phase 3 — Full Remote Controls

- [ ] Power where supported
- [ ] Input/source selection
- [ ] Channel up/down
- [ ] Numeric keypad
- [ ] Play/pause
- [ ] Rewind/fast-forward
- [ ] Additional platform-specific buttons
- [ ] Text/keyboard input where supported

## Phase 4 — Multiple Hisense Platforms

- [ ] VIDAA adapter
- [ ] Roku TV adapter
- [ ] Android TV / Google TV adapter
- [ ] Capability detection
- [ ] Hide or disable unsupported commands cleanly

No platform will be marked supported until tested against real hardware or a trustworthy protocol test environment.

## Phase 5 — User Experience

- [ ] Haptic feedback
- [ ] Dark/light/system themes
- [ ] Multiple saved TVs
- [ ] Customizable button layout
- [ ] Favorite inputs/apps
- [ ] Accessibility review
- [ ] Tablet/foldable layout review

## Phase 6 — Android Integrations

Possible additions after the core app is stable:

- [ ] Home-screen widget
- [ ] Quick Settings tile
- [ ] Wear OS companion
- [ ] App shortcuts

## Phase 7 — Release Readiness

- [ ] Privacy policy
- [ ] Play Store listing
- [ ] Screenshots and app artwork
- [ ] Release signing
- [ ] Crash/error review
- [ ] Network permission review
- [ ] Dependency/license audit
- [ ] Beta testing
- [ ] Version 1.0 release

## Non-Goals for Early Versions

The following should not distract from a reliable local remote:

- cloud accounts
- social features
- remote control over the public Internet
- subscriptions for basic remote functions
- advertising SDKs
- unnecessary analytics

## Release Philosophy

A smaller feature that works reliably is preferred over broad device support that only works intermittently. New protocols and features should be added incrementally and should not destabilize existing television support.
