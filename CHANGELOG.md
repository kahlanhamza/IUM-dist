# Changelog

All notable user-facing changes to IUM are documented here. Versioning follows
[Semantic Versioning](https://semver.org/).

## [0.2.2] — 2026-11-11

### Changed
- **The distribution moved to this public repo.** The updater feed (`latest.json`)
  and every download link now live at
  [kahlanhamza/IUM-dist](https://github.com/kahlanhamza/IUM-dist) — releases and
  auto-updates keep working no matter where the development happens.
- The installer's copyright notice states the real terms (© 2026 IUM. All rights
  reserved) — it previously claimed an incorrect MIT license.

### Fixed
- Auto-update survived the move: from v0.2.2 the update feed is public and the
  built-in updater works permanently. Installs from v0.2.1 or earlier need one
  final manual update (download, verify, install over the old version) — see
  [the README](README.md#updates).

## [0.2.1] — 2026-11-10

### Fixed
- A known SQLite vulnerability (CVE-2026-119375, CVSS 6.8) in the component that
  stores the upload journal was upgraded past the affected versions. Existing
  journals open unchanged — upgrading does not touch your data.

### Added
- The [User Guide](USERGUIDE.md): download → verify → install → first upload →
  troubleshoot, with per-OS checksum commands and the security-warning walkthrough.

### Changed
- The desktop README and the app's "About" metadata state the real license terms
  (proprietary).

## [0.2.0] — 2026-11-08

The design-and-manners release: the completed **Ink** visual program, the ⌘K
command palette, Windows 11 Mica support, OS notifications, a global speed cap,
the account-connected destination lanes (WebDAV, Google Drive, YouTube), painless
authentication (OS keychain vault, hot lane switching, test-connection), signed
auto-update, and the first public release set: installers for Linux (deb / rpm /
AppImage), macOS Apple Silicon (dmg) and Windows (msi / NSIS setup).
