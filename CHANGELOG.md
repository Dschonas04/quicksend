# Changelog

All notable changes to Quicksend. The format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/), versions follow
[Semantic Versioning](https://semver.org/).

## [Unreleased]

## [1.1.1] - 2026-10-05

### Security
- The user interface compared the `Origin` of a write request as a
  substring, so `http://localhost.example.com` passed. It now accepts only
  a host that is exactly `localhost`, `127.0.0.1` or `::1`. Modern browsers
  were already stopped by the `Sec-Fetch-Site` check.

### Changed
- Dependencies updated: `golang.org/x/net` 0.59, `golang.org/x/sys` 0.48,
  `miekg/dns` 1.1.73. Building now needs Go 1.26.
- Workflows build with the latest stable Go.

## [1.1.0] - 2026-09-28

### Security
- Wrong device codes cost time: after five misses an address waits
  30 seconds, doubling per further miss up to 15 minutes, forgotten after
  an hour of quiet. The answer carries `Retry-After`.
- The user interface refuses any `Host` other than loopback (DNS
  rebinding), turns away cross-site writes and sends a strict content
  security policy.
- Releases carry build provenance attestations; the macOS bundle has an
  ad-hoc signature.

### Fixed
- A data race between the send queue and its caller.
- A manual release run produced the version `main1.0.0`.

## [1.0.0] - 2026-09-28

### Added
- Send files to another computer on the same network: discovery over mDNS,
  TLS with certificate pinning, a six-digit code per device.
- Transfers resume by byte after a dropped connection or a restart; the
  send queue survives a crash; files are checked with SHA-256 before they
  are moved into place.
- Single binaries for Windows, macOS (`.dmg`) and Linux.

[Unreleased]: https://github.com/Dschonas04/quicksend/compare/v1.1.1...HEAD
[1.1.1]: https://github.com/Dschonas04/quicksend/compare/v1.1.0...v1.1.1
[1.1.0]: https://github.com/Dschonas04/quicksend/compare/v1.0.0...v1.1.0
[1.0.0]: https://github.com/Dschonas04/quicksend/releases/tag/v1.0.0
