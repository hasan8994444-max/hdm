# Download Craft 0.9.11

## What's new

**App**
- **Updates itself**: when a new release is out, the portable app downloads it, checks it against the
  checksum GitHub publishes, replaces every file in its folder and restarts into the new version — after
  the downloads that are running have finished. If anything fails, nothing is changed and the Update
  button stays for another try.
- **Ready on first start**: yt-dlp, FFmpeg and Deno (the JavaScript runtime YouTube needs) download in the
  background the first time the app opens, so the first video download does not stop to fetch them.
  This also fixes YouTube videos arriving in 360p when 1080p was picked: without FFmpeg, YouTube only
  offers 360p as a single file. Helpers you pointed at your own copy in Settings are left alone.
- **Progress window**: **Cancel** while downloading (it stops like the main window's Stop and keeps the
  partial file); closing the window pauses the download; minimising it keeps it going.
- **"Download Craft isn't running"**: pressing Download in the browser's download window while the app is
  closed now says so and queues nothing. Clicks made while the app was closed no longer all start the
  next time it opens.
- **DRM-protected videos** (Widevine and the like, e.g. paid streaming sites) are recognised: instead of a
  file with no picture or sound, the download stops with a clear message and the broken file is removed.
  Protected videos are never worked around.

**Browser extension**
- **Qualities in the popup**: the files a video player loaded are one card with a quality list — 1080p,
  720p, 480p… — read from each file's header, instead of several cards that all said "MP4".
- **The video button opens its menu** with the quality you picked last already selected; picking another
  one changes the button to "Download 720p" right away. The separate ▾ is gone.
- DRM-protected videos show a short explanation instead of a download that would not play.

## Updating from 0.9.10

Use **Update now** in the app: it downloads this release, checks it and restarts. Then reload the browser
extension (chrome://extensions → reload) with the files from this release.

## Install

**Windows 10/11.** Extract `DownloadCraft-0.9.11-windows-x64-portable.zip` and run `download_craft.exe` —
nothing to install. Your queue and settings in `%APPDATA%\download_craft` carry over.

**macOS 12+.** Unzip `DownloadCraft-0.9.11-macos-Universal.zip` and move `Download Craft.app` into
Applications. This development build is not notarized: right-click → Open the first time.

**Linux (x86-64, glibc 2.28+).**
- Ubuntu, Debian, Mint, Pop!_OS: `sudo apt install ./downloadcraft_0.9.11_amd64.deb`
- Fedora: `sudo dnf install ./downloadcraft-0.9.11-1.x86_64.rpm`
- Other distributions: `DownloadCraft-0.9.11-x86_64.AppImage` (mark it executable; without FUSE run it
  with `--appimage-extract-and-run`).

**Browser extension (0.9.11).**
- Chrome / Edge / Brave: extract `DownloadCraft-Chrome-0.9.11.zip`, open `chrome://extensions`, enable
  Developer mode, **Load unpacked** → the `browser-extension` folder. Already installed? Press reload on
  the extension and refresh open tabs.
- Firefox: `about:debugging#/runtime/this-firefox` → **Load Temporary Add-on…** →
  `DownloadCraft-Firefox-0.9.11.xpi` (unsigned).
- Then in the app: Settings → Browser Integration → **Install** for your browser.

## Media helpers

Settings → Plugins downloads and updates **yt-dlp**, **FFmpeg + ffprobe** and a portable
**JavaScript runtime** (Deno) into the app's own folder — no installers, no PATH changes, no sudo.
System copies on PATH or a custom file can be chosen instead.

RAR archives are read with the UnRAR source code (freeware licence, extraction only); see `NOTICE.md`.
