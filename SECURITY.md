# Security Policy

Polaris Remote communicates with televisions over local networks, so networking and pairing behavior should be treated as security-sensitive.

## Reporting a Vulnerability

Please avoid publishing exploitable security details in a public issue before a fix is available.

If a private reporting channel is configured for the repository, use it. Otherwise, open a minimal issue stating that you have identified a potential security problem without including secrets, credentials, exploit payloads, or sensitive device information.

## Sensitive Information

Never commit or post:

- Wi-Fi passwords
- pairing credentials or tokens
- signing keys or keystores
- private certificates or keys
- API credentials
- personally identifying user data

## Security Expectations

Changes involving networking, discovery, pairing, authentication, storage of credentials, or Android permissions should receive extra review.

Production code must not disable TLS certificate validation as a shortcut, accept arbitrary certificates without a documented protocol requirement and safe design, or store authentication material in plain text when secure Android storage is appropriate.

## Supported Versions

Security fixes will target the current development version and currently maintained releases once public releases begin. A formal supported-version table will be added after the first stable release.
