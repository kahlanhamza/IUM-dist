# Changelog

All notable user-facing changes to IUM are documented here. Versioning follows
[Semantic Versioning](https://semver.org/).

## [0.2.5] — 2026-11-14

### Fixed
- **The connect sheets render one field per row**: Settings → connections
  no longer crams several credential fields side by side; every field sits
  on its own row, labels wrap instead of painting over each other, and the
  S3 bucket-URL field is one clear line of copy (the example lives in the
  note above it).
- **The settings dialog and command palette stay opaque under Windows 11
  Mica**: the dialog no longer prints the app content and wallpaper
  through itself; what you read sits on a solid layer.
- **Connect no longer opens a console window or a broken sign-in page**:
  the sign-in page opens in your browser with the full request attached —
  the scope Microsoft was refusing to see is back — and every background
  helper hides its console window.
- **First-launch reliability**: a cold first boot no longer strands the
  app on "engine unreachable"; the interface retries within the boot
  window and recovers on its own, so even a slow 30-second cold start
  reaches a working window without a restart.

## [0.2.4] — 2026-11-14

### Added
- **Native Dropbox connector**: sign in from the app with IUM's own OAuth app
  identity — your browser, your Dropbox account, no shared app password.
  Uploads run as resumable chunked-append sessions; a job interrupted
  mid-flight resumes on its journaled session id with the server's own
  answer correcting any drifted offset; and a job reaches Done only after
  the finished object's `content_hash` matches what Dropbox stored.
- **Native OneDrive connector**: the same shape for OneDrive and OneDrive
  for Business. Entra sign-in with IUM's own public-client identity,
  Microsoft Graph upload sessions carrying uniform 5 MiB fragments,
  server-wins realign on any drifted offset, and verify-before-declare
  against the server's `quickXorHash`.

## [0.2.3] — 2026-11-11

### Added
- **The destination picker.** The upload form now leads with "where should files
  go?" — pick a known provider (Backblaze B2, Cloudflare R2, Wasabi, Scaleway,
  DigitalOcean Spaces, Filebase, self-hosted MinIO), name your bucket, and the
  destination URL builds itself. Each provider carries a deep link to its key
  console and a short recipe. Custom URL stays the default: paste any
  destination exactly as before.
- **A working Test button for S3 lanes.** Check your keys and bucket before the
  first job — IUM opens and aborts its own tiny probe session, so the check
  never touches your objects.
- **Expiring share links.** A finished S3 upload can hand you a signed download
  link that opens for 24 hours and then expires — minted on demand from your
  own keys; nothing is made public until you ask.
- **The guided region is the signing region.** The region you pick in the form
  is remembered for the lane, so the request signature always matches the
  destination.

### Fixed
- **The provider list matches the providers' own current documentation.**
  Filebase's general S3 endpoint is `s3.filebase.io`; Wasabi offers all 16
  documented regions; DigitalOcean Spaces all 13; Backblaze B2 gained
  `us-east-005` and dropped an uncorroborated region.

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
