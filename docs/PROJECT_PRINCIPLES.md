# Project Principles

Polaris Remote exists to provide a useful, respectful, and dependable Android remote-control experience.

## 1. Core Remote Features Stay Free

Basic local remote functionality should not be locked behind a subscription. Users should be able to connect to a supported television and use normal remote controls without paying recurring fees.

## 2. Local First

Whenever the television platform allows it, control should happen directly between the Android device and television over the local network.

Cloud infrastructure should not be introduced unless a future feature genuinely requires it and the user clearly understands the tradeoff.

## 3. No Account Required for Normal Use

Users should not need to create an account simply to control a television on their own network.

## 4. Privacy by Default

Polaris Remote should collect as little information as possible.

Do not add invasive analytics, tracking SDKs, advertising identifiers, or unrelated data collection merely because they are easy to add.

## 5. Minimum Permissions

Request only Android permissions required by implemented features. Every permission should have a clear explanation and should be removed if the feature no longer needs it.

## 6. Reliable Before Broad

A small number of thoroughly tested television platforms is better than claiming universal compatibility that does not work reliably.

Compatibility claims must be based on evidence and testing.

## 7. Protocol Isolation

Television-specific protocols belong behind common interfaces. UI components and application business logic should not contain raw vendor protocol handling.

This allows platforms to evolve independently and reduces regressions.

## 8. Graceful Failure

A television being offline, unsupported, unpaired, or unreachable must not crash the application. Errors should explain what happened and, where practical, what the user can do next.

## 9. Security Is Not a Shortcut

Do not disable certificate validation, hard-code secrets, expose pairing credentials, or weaken Android security controls merely to make development easier.

## 10. Keep the App Lightweight

Avoid unnecessary libraries, background services, cloud calls, and abstractions. Every dependency and persistent process should justify its cost.

## 11. Accessibility Matters

Controls should be usable with Android accessibility tools. Touch targets, labels, contrast, focus order, and alternative interaction methods should be considered throughout development rather than added only at the end.

## 12. Honest Compatibility

If a feature or television platform is experimental, say so. If a command cannot work on a particular platform, the app should not pretend otherwise.

## 13. Independent Project

Polaris Remote is an independent open-source project. References to Hisense and television operating-system brands describe compatibility only and do not imply endorsement, partnership, or affiliation.

## 14. Build in Small Working Steps

Development should favor milestones that can be tested end-to-end. The first goal is not a universal remote; it is a small remote that successfully controls a real television.
