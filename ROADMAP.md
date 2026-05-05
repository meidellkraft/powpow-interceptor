# Roadmap

Planned improvements and future directions for PowPow Interceptor.

Items are loosely ordered by priority. Nothing here is committed or scheduled — it reflects current thinking.

---

## Store Publishing

### Chrome Web Store

Publish the extension to the [Chrome Web Store](https://chromewebstore.google.com/) so users can install it without manually downloading and loading unpacked ZIPs.

What's needed:
- Google Developer account and one-time $5 registration fee
- Chrome Web Store OAuth credentials (`CHROME_CLIENT_ID`, `CHROME_CLIENT_SECRET`, `CHROME_REFRESH_TOKEN`) and the assigned extension ID (`CHROME_EXTENSION_ID`)
- Re-add a publish step to the CI workflow (previously removed while the store listing is being set up)
- Store listing: description, screenshots, privacy policy

The CI infrastructure for building and zipping the extension is already in place. Publishing is a single additional step once the store listing exists.

### Microsoft Edge Add-ons

Publish to the [Microsoft Edge Add-ons](https://microsoftedge.microsoft.com/addons/) store. Edge supports Chrome Manifest V3 extensions natively, so the same built artifact can be submitted without changes.

What's needed:
- Microsoft Partner Center account
- Edge Add-ons API credentials for automated publishing
- Store listing: description, screenshots, privacy policy (can largely mirror the Chrome listing)

---

## Features

### Firefox support

Firefox supports Manifest V3 as of Firefox 109. The `chrome.debugger` API is Chrome-specific, but Firefox has an equivalent (`browser.debugger`) that may allow a compatible implementation. This would require evaluating API parity and potentially shipping separate builds.

### Per-file toggle

Allow individual web files or templates to be toggled on/off without disabling the entire extension. Useful when only some files have local changes.

### Popup dev server log

Surface recent interception events (matched file name, response time) directly in the popup to make it easier to confirm which files are being intercepted.
