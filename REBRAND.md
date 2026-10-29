# HDM — Rebrand notes

**HDM (Hasan Download Manager)** by **Hasan**.
Rebranded 2026-10-29 from the open-source project **DownloadCraft**
(https://github.com/hungry-detective/downloadcraft), version 0.9.12, MIT License.

## What changed
- Product name everywhere user-visible: DownloadCraft / Download Craft -> **HDM**
- Binary: `download_craft(.exe)` -> `hdm(.exe)`; Rust package `hdm`; engine crate
  `crates/downloadcraft-engine` -> `crates/hdm-engine` (`hdm_engine`)
- Config folder: `%APPDATA%/download_craft` -> `%APPDATA%/hdm`
- Browser native-messaging host: `com.download_craft` -> `com.hdm`
  (extension and desktop app renamed together, so they still pair)
- Browser extension name/menus: "Send to HDM", "Download with HDM"
- Premium UI: deep navy-black surfaces, gold accent (#D4AF37) primary,
  champagne secondary, softer 12px corners, gold primary buttons,
  warm-ivory light theme, matching gold accents in the extension UI
- About window: "by Hasan" byline + an **Upstream** credit link

## What was deliberately kept
- `LICENSE` — the original "Download Craft contributors" copyright line is
  preserved under Hasan's line, as the MIT License requires.
- `NOTICE.md` — third-party notices (UnRAR, fonts, crates) unchanged in substance.
- Site-rules URL still points at the upstream file so the extension keeps
  receiving site rules (the file is data, not branding).

## Before publishing to GitHub (one step only Hasan can do)
The code contains the placeholder `HASAN-USERNAME` in GitHub URLs
(README badges, About links, update check). Replace it with Hasan's real
GitHub username in all files, e.g.:
`grep -rl HASAN-USERNAME . | xargs sed -i 's/HASAN-USERNAME/<username>/g'`
Until then the in-app update check simply reports that it cannot reach
releases — everything else works fully offline.
