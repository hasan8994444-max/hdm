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
The code contains the placeholder `hasan8994444-max` in GitHub URLs
(README badges, About links, update check). Replace it with Hasan's real
GitHub username in all files, e.g.:
`grep -rl hasan8994444-max . | xargs sed -i 's/hasan8994444-max/<username>/g'`
Until then the in-app update check simply reports that it cannot reach
releases — everything else works fully offline.

## Universal page resolver (added Oct 30, 2026)

Prompted by sites whose videos the first release missed, HDM's page
resolver was extended with the extraction *patterns* used by mobile
downloaders (the technique was studied in Hasan's HTube app — an
Android, GPL-3.0 project — and re-implemented here from scratch in
original Rust; no GPL code was copied, so HDM stays MIT):

- Social player JSON fields, HD first: `browser_native_hd_url`,
  `playable_url_quality_hd`, `hd_src`/`sd_src` (+ `_no_ratelimit`),
  `playable_url`, TikTok `playAddr`/`downloadAddr`, `video_url` —
  with site interface assets (rsrc.php / static CDNs) filtered out.
- `mediaDefinitions` quality lists (highest quality wins) and
  `setVideoUrlLow/High` player calls from tube sites.
- Player-declared HLS only (`hlsUrl`/`hls`/`manifestUrl` keys,
  `setVideoHLS`) — a merely linked or meta-tagged playlist is still
  not treated as the page's stream.
- X / Twitter: the public tweet-widget endpoint (base36 token) picks
  the highest-bitrate MP4 variant.
- Reddit: the public embed page reveals the `v.redd.it` id, whose
  HLS playlist is then downloaded and muxed like any other HLS.
- Mobile retry: if the desktop scan finds nothing, the page is
  fetched once more under a mobile user-agent, because many sites
  only hand their player JSON to mobile browsers.
