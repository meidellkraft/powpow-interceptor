# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.1.1] - 2026-05-05

### Changed

- Migrated repository to [itera-fredrikstad/powpow-interceptor](https://github.com/itera-fredrikstad/powpow-interceptor)
- Replaced manual Chrome Web Store publish workflow with an automated CI workflow that builds on every push to `main` and creates a GitHub release when the version in `package.json` is bumped
- Version consistency is now enforced in CI: the build fails if `package.json` and `public/manifest.json` versions differ

## [0.1.0] - 2026-04-13

### Added

- **Web file interception** — JS and CSS requests are matched against the PowPow CLI manifest and fulfilled from the local dev server, bypassing the portal
- **Web template injection** — HTML document responses are scanned for `<script data-webtemplate-id="...">` blocks; matching blocks are replaced with local dev server content
- **Automatic tab attachment** — `chrome.debugger` attaches to all open and newly navigated tabs whose URL matches the configured portal hostname
- **Global on/off toggle** — enable or disable all interception with a single click in the popup
- **Status indicator** — shows manifest load state (connected / loading / unreachable / disabled), loaded file and template counts, and number of intercepted tabs
- **Persistent settings** — dev server port and target portal hostname are saved to `chrome.storage.local` and restored across browser restarts
- **Auto-reconnect** — the popup automatically reconnects to the background service worker if the connection drops
