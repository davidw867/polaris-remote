# Protocol Support

Hisense sells televisions using multiple operating systems and control protocols. A model being manufactured by Hisense does not guarantee that it uses the same remote protocol as another Hisense model.

Polaris Remote therefore tracks support by platform and tested behavior.

## Support Levels

- **Planned** — intended for investigation or implementation.
- **Experimental** — implementation exists but has limited hardware testing.
- **Supported** — core controls have been tested successfully on real hardware.
- **Unsupported** — known not to work or intentionally excluded.

## Current Matrix

| Platform | Status | Discovery | Pairing | Basic Navigation | Volume | Power | Notes |
|---|---|---|---|---|---|---|---|
| Hisense VIDAA | Planned | TBD | TBD | TBD | TBD | TBD | Protocol research and hardware testing required. |
| Hisense Roku TV | Planned | TBD | TBD | TBD | TBD | TBD | Expected to require Roku-specific adapter behavior. |
| Hisense Android TV / Google TV | Planned | TBD | TBD | TBD | TBD | TBD | Requires Android/Google TV remote protocol investigation and testing. |

No platform is currently claimed as supported because implementation and hardware validation have not yet been completed.

## Testing Record Template

When validating a protocol, record:

```text
Manufacturer: Hisense
Model:
Region:
TV platform / OS:
TV software version:
Polaris Remote version/commit:
Android device:
Android version:
Discovery: PASS / FAIL / N/A
Pairing: PASS / FAIL / N/A
Navigation: PASS / FAIL
Volume: PASS / FAIL / N/A
Mute: PASS / FAIL / N/A
Home: PASS / FAIL
Back: PASS / FAIL
Power on: PASS / FAIL / N/A
Power off: PASS / FAIL / N/A
Input selection: PASS / FAIL / N/A
Playback: PASS / FAIL / N/A
Notes:
```

## Capability Model

The application should not assume every connected television supports every command. Each adapter should expose capabilities so the UI can hide, disable, or explain commands that the current device does not support.

Examples:

```text
POWER_ON
POWER_OFF
VOLUME
CHANNELS
NUMERIC_INPUT
TEXT_INPUT
APP_LAUNCH
INPUT_SELECTION
PLAYBACK
```

## Protocol Documentation Rules

For each implemented adapter, document:

- discovery mechanism
- network transport and ports where appropriate
- pairing/authentication requirements
- connection lifecycle
- command mapping
- known limitations
- tested television models

Do not include private credentials, pairing secrets, or copyrighted/vendor-confidential material in this repository.

## Trademark Notice

Platform and product names are used solely to describe compatibility. Polaris Remote is not affiliated with or endorsed by Hisense, Roku, Google, or VIDAA platform owners.
