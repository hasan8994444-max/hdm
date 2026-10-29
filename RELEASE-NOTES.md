# Download Craft 0.9.12

## What's new

**Setting up**
- **Get ready**: a small window lists what Download Craft needs — the browser connection, the
  browser extension, yt-dlp, FFmpeg and Deno — with what each is for and whether it is ready. Each has
  its own Install / Set up button, and **Fix everything** does them all. The extension row shows the
  three steps to add it, with **Open folder** and **Copy path**. The window opens at start-up only when
  something is missing (it fixes what it can by itself) and any time from **Help → Get ready…**.

**Downloads**
- **A head start, as in IDM**: while the Download File Info window is open, a plain file already
  downloads in the background. Press Download and it continues under the name and folder you chose,
  so the progress window opens partway through. Cancel deletes what was fetched. (Video pages and
  streams still start when you press Download.)
- **"Download Craft isn't running"** now shows as soon as the Download File Info window opens, and
  goes away by itself once the app starts. A file already in the list starts and the window closes.
- **Drag finished downloads out of the list** onto a folder, the desktop, a chat or a mail; select
  several to drag them together.
- Opening the browser no longer captures downloads from its last session again.

**Windows**
- **About & Updates** is its own small window: up to date, update available (with highlights from the
  release notes), installing (each step), ready to restart. An **Update automatically** switch decides
  whether new versions install by themselves. It also lists your helpers and links to GitHub,
  release notes, issues and licenses.
- **Progress window**: a bolder progress bar; the Speed tab has one row for the speed limit with a
  **KB/s / MB/s** choice (the unit used to be unstated) and a clearer graph with the current and peak
  speed.
- **Download all links**: search, type chips and "Hide web pages" in one aligned row that wraps only
  when it must, so more files fit; the main list's outline file icons; dragging a column moves the
  ones after it, and nothing runs outside the table; the status line spans the window.
- **Download complete** uses the app's dark colours.
- An update also removes files the new version no longer has (an old Firefox .xpi, for example).

**Look**
- Dark mode: the sidebar and the list are a step brighter than the window, as in light mode; the
  title bar keeps the window's colour.
- The Name column has an icon like the others; **Settings → Appearance → Hide column icons** shows the
  titles alone, at once.
- Search opens when you click the magnifier (pointing at it no longer opens it).

**Browser extension**
- The video button says just **Download**; its menu opens with the quality you use most selected.
- It stays inside the player when you point at it, is a little shorter, and hides while a site's
  pinned header (Facebook's top bar) covers it, as IDM's does.

## Updating from 0.9.11

Use **Update now** in the app: it downloads this release, checks it and restarts. Then reload the browser
extension (chrome://extensions → reload) with the files from this release.

## Install

**Windows 10/11.** Extract `DownloadCraft-0.9.12-windows-x64-portable.zip` and run `download_craft.exe` —
nothing to install. Your queue and settings in `%APPDATA%\download_craft` carry over.

**macOS 12+.** Unzip `DownloadCraft-0.9.12-macos-Universal.zip` and move `Download Craft.app` into
Applications. This development build is not notarized: right-click → Open the first time.

**Linux (x86-64, glibc 2.28+).**
- Ubuntu, Debian, Mint, Pop!_OS: `sudo apt install ./downloadcraft_0.9.12_amd64.deb`
- Fedora: `sudo dnf install ./downloadcraft-0.9.12-1.x86_64.rpm`
- Other distributions: `DownloadCraft-0.9.12-x86_64.AppImage` (mark it executable; without FUSE run it
  with `--appimage-extract-and-run`).

**Browser extension (0.9.12).**
- Chrome / Edge / Brave: extract `DownloadCraft-Chrome-0.9.12.zip`, open `chrome://extensions`, enable
  Developer mode, **Load unpacked** → the `browser-extension` folder. Already installed? Press reload on
  the extension and refresh open tabs.
- Firefox: `about:debugging#/runtime/this-firefox` → **Load Temporary Add-on…** →
  `DownloadCraft-Firefox-0.9.12.xpi` (unsigned).
- Then in the app: Settings → Browser Integration → **Install** for your browser.

## Media helpers

Settings → Plugins downloads and updates **yt-dlp**, **FFmpeg + ffprobe** and a portable
**JavaScript runtime** (Deno) into the app's own folder — no installers, no PATH changes, no sudo.
System copies on PATH or a custom file can be chosen instead.

RAR archives are read with the UnRAR source code (freeware licence, extraction only); see `NOTICE.md`.
