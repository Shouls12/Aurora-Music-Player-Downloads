# Aurora Music Player — Changelog

## [0.1.7] — Current Release

### Added
- Track Info now writes metadata and embedded cover art back to MP3 (ID3v2), FLAC and Ogg Vorbis files, with atomic replacement and a clear library-only fallback for unsupported formats. The write can be disabled in Preferences ▸ Backup & Data ▸ File metadata.
- Smart playlists: an all/any rule builder over title, artist, album, album artist, genre, format, year, rating, play count, duration, favorite and date fields, with a live match preview, sorting and a track limit. Smart playlists recalculate as the library changes, and can be edited from their card, detail page or actions menu.
- In-app notifications can be disabled in Preferences ▸ Appearance ▸ Application.

### Changed
- The playlists overview distinguishes manual and smart playlists, shows rule summaries, and keeps manual membership actions separate from rule-driven lists.
- The release test suite now covers tag-result IPC/UI, smart-playlist resolution, saving and editor behavior, packaged title-bar and About version reporting, and notification stacking/suppression.
- `npm run test:sweep` runs the whole release gate in order: development suites, then the Windows installer and portable executable, and only when both are green does it rebuild the AppImage and test it last. The AppImage suite now refuses to run against an image older than the current source.
- The sweep now covers the surfaces that were previously unguarded: the 10-band equalizer (presets, live filter gains, disable, reset, saved presets), track and playlist context menus, the sleep timer through real expiry, bulk rating/favorite/add-to-playlist/removal, online result mapping onto Track Info, and native window state (title, taskbar progress, maximize, fullscreen).
- `node scripts/ipc-coverage.js` requires every IPC channel to be proven by a suite or allowlisted with a reason, and fails on a new unproven channel, so release coverage cannot silently decay.
- Distribution readiness is the sweep's final stage: it verifies the installer, portable and AppImage, writes `dist/SHA256SUMS.txt` and `dist/release-manifest.json`, and enforces the documentation check. `npm run release` runs the sweep and refuses to publish when any stage is red.
- The sweep is self-sufficient on Windows: the AppImage step builds through `npm run build:linux:wsl`, which copies the tree into an isolated WSL directory, installs the Linux dependencies there and uses a private Linux Node (`~/.local/aurora-node`, downloaded automatically when the distro has none), so the Windows `node_modules` is never replaced and no manual Linux setup is required.
- The release sweep grew automated coverage for native dialogs, drag-and-drop, media keys, the tray, single instance, corrupt-data recovery, 0.1.6 data migration, accessibility (tree and keyboard-only), a 20,000-track library, soaking, the Windows installer, and the AppImage. The AppImage suite can now run on Windows through WSL, and the installer suite verifies registration, file associations, upgrades and uninstall.

- The title bar no longer carries Library, Playback and View menus; Preferences now sits in the sidebar footer beside Managed Libraries at the same size as the add-folder button. Everything those menus did throughout now lives where it belongs: Add Files/Folder in the header and Music Folders, Import/Export playlist in Backup & Data, and the sleep timer in Audio. Queue, lyrics, visualizer, mini player, theme, density and grid/list already had homes in the player bar and Appearance.

### Fixed
- The Track Info “Metadata ready — Save to apply” notification now stays above open dialogs and their blurred backdrop.
- Drag-and-drop works again: Electron 32+ removed `File.path`, so dropped files are resolved through `webUtils.getPathForFile` in the preload bridge.
- Opening an audio file while the app is still starting no longer loses it; opened files are queued until the renderer has loaded its library.
- Pausing now clears the Windows taskbar progress instead of leaving it stuck at the last position. The clear runs on the UI pause path (play button, spacebar, media keys and the sleep timer), not in the audio `pause` event, which also fires for track changes and blanked the visualizer.
- The Keyboard Shortcuts dialog now moves focus into the dialog when it opens.

## [0.1.6] — Previous Release

### Added
- A dedicated Duplicate Finder window, opened from Preferences ▸ Help, that scans matching title, artist, album and duration metadata. It suggests the highest-quality copy to keep, supports per-copy selection, Keep best, Select extras and Clear, removes library entries only by default, and offers an explicit permanent file-deletion option with per-file failure reporting.
- Appearance presets and quick accent swatches, plus startup-view and sidebar-width workspace preferences.
- Backup and restore for settings, playlists and the library index (Preferences ▸ Help ▸ Data); every restore snapshots the current data to `backups/` first.
- Multi-select in the track list: click, Ctrl/Cmd-click and Shift-click for a range, with a bulk bar for favorite, rating, add to playlist and remove.
- A real Playlists overview with automatic-playlist cards, user playlist cards, cover mosaics, hover Play and an overflow action menu.
- Detail pages for albums, artists, genres, folders and playlists with artwork, Play/Shuffle actions, a sticky toolbar, breadcrumb back navigation and compact rows.

- Loading skeletons and determinate scan/import progress with cancellation; list, grid and detail destinations now share page headers and designed empty states.
- Batch 3 feedback and navigation: typed success/info/warning/error toasts with hover-pause and optional Undo, a cancelable sleep-timer chip, and Managed Libraries folder browsing with a deduplicated folder list.

### Added
- **Minimize to system tray** preference in Preferences ▸ Appearance, enabled by default; turning it off lets Close exit and Minimize use the taskbar.

### Changed
- Release builds now produce and verify the Windows installer, Windows portable executable and Linux AppImage, launch-test the AppImage, and publish the matching changelog with each release.
- The track list is virtualized: only rows in and near the viewport exist in the DOM. 200 rows render in 3–16 ms (was ~183 ms) and 2,000 rows in 4–18 ms; album, artist, genre and folder detail views use the same windowing.
- What's New now opens on the current release only, with a collapsed archive for every older release. About uses a compact identity card with the app mark, version, creator and AI-assistance note instead of a full-width banner.
- The title bar now has three task-based menus — Library, Playback and View — plus a direct Preferences button. Transport actions stay in the player bar, Managed Libraries stays in the sidebar, Duplicate Finder lives in Preferences ▸ Help, and Keyboard Shortcuts lives in Preferences ▸ Help and `?`.
- The title bar centers the app name and insets the window controls from the right edge while keeping the menus left-aligned.
- The track list fills its width with a flexible title column and a sticky, sortable header; playing rows now use an accent bar and equalizer while selected rows use a neutral surface.
- The player bar is one transport row with SVG controls, full-width seek and time labels, a queue icon, and a working mute button.
- Preferences fills the workspace, remembers the last-used tab and adds a search field that jumps to and highlights matching settings. Seven tabs are grouped under Personalize, Playback, Library and Support, with arrow-key navigation and clearer section titles. Volume, playback speed, shuffle/repeat, equalizer access, browse layout and track-column controls now live in Preferences instead of only in menus or the player bar. The two onboarding toggles moved from Overlays into Appearance ▸ Application.
- The mini player is a compact 360×200 card capped at 520×280, with an integrated drag header and window controls plus the current SVG transport, seek, timestamps, shuffle, repeat, favorite, volume and overflow controls.
- The visualizer is a framed Aurora stage between the title bar and player bar, with an idle state, a themed mode picker grouped by Spectrum, Waveform, Motion and Atmosphere, and fullscreen control. Each mode now remembers its own color mode. Windowed mode uses the player-bar track identity and leaves transport and seek there; fullscreen shows the glass now-playing card, transport and progress HUD. The 18 renderers include new Pulse Grid, Lissajous and Audio Rain modes, all using the active color palette and aggregate FFT bands so narrow frequencies do not leave blank bars. F11 or the fullscreen button toggles edge-to-edge mode.
- Queue and lyrics panels have counts, loading/empty/error feedback, drag-to-reorder, play-next, click-to-seek lyrics and lyric font controls.
- The player-bar sidebar button now opens and closes the right panel and returns to the tab you last used, Queue or Lyrics; that choice is saved across restarts.

- The queue is virtualized for long queues, dialogs trap Tab focus, the mini player has an overflow menu, and visualizer mode is saved. Preferences gained compact Libraries rows and a Data snapshot browser with read-only preview and restore.

- Batch 2 polish: retryable error states, a shared control kit, Libraries overflow actions, Track Info loading/empty/error handling, explicit queue drag handles, visualizer artwork, mini-player metadata persistence while controls auto-hide, and light-theme surface fixes.
- Batch 3 foundations: shared color/type/spacing/radius/elevation tokens, accent-derived surfaces, a light-mode transport, a visible focus ring, labelled dialogs, nav/row/sort ARIA, reduced-motion scrolling, and compact layouts down to 320 px.

### Fixed
- The Keyboard Shortcuts footer **Close** button now closes the dialog; every `data-close` action shares the same close handler instead of only header ✕ buttons.
- The main header now uses the same themed surface as the sidebar and player instead of showing the aurora body through it.
- The mini player no longer opens at 420×720, grow beyond 520×280 or use the old Unicode control glyphs; its title bar and window controls now live inside the card, and the window/tray fallback loads `build/icon.ico` instead of a missing legacy logo path.
- Playlists search now filters playlist names and updates the header count; detail pages hide the library search instead of showing a field that cannot affect their fixed contents.
- Fixed the detached column strip losing its row layout, album grid rows stretching to fill the viewport, and Preferences not opening from its shared command helper.
- Playlists now uses the main header for its title, saved-track count and New Playlist action instead of repeating a second page title; tablet layouts keep Duration visible, and mini/visualizer modes hide the column strip.
- Recently Added is now only a built-in automatic playlist; the duplicate sidebar tab and its unused day-window preference were removed.
- The column strip now sits in its own sub-header above the list scroller, so it spans the full window and the scrollbar starts below it; the title column header no longer disappears in narrow layouts.
- Track-list column headers now own sorting (click or Enter/Space, click again to reverse), drag-to-reorder and width resizing; the separate Sort and direction buttons were removed from the main header, while the strip keeps the flush header surface.
- Collection counts and the Add music action now live in the main header for All Tracks, Albums, Artists and Genres; the separate title/count/action row was removed, leaving more room for content.
- Grid page headers now span the full content row, removing the dead space and stretched first card in Albums, Artists and Genres.
- The sidebar banner was removed; the Aurora banner now appears only in the first-run Welcome overlay. About and What’s New use compact brand marks instead. Sidebar navigation spacing was tightened.
- Managed Libraries deduplicates folder paths case-insensitively on load and save, preserving scan settings and track counts.
- The redundant Folders sidebar item was removed; folder tracks open from a Managed Libraries row.
- What's New now opens above Preferences. Esc dismisses the top layer first, and the in-app release notes include 0.1.6.
- The queue/lyrics side panel had a 4 px gap above the player bar; it now meets the player exactly.
- Native alert/confirm/prompt dialogs were replaced with themed dialogs that resolve on Esc, backdrop, × and action buttons.
- Shift-click ranges in the album, artist, genre and folder detail views used the last main-list order, so a short range could select unrelated tracks.
- Bulk favorite now refreshes the heart icons immediately instead of waiting for the next render.
- Playback scrolls the currently playing row into view again when it sits outside the virtualized window.
- Global shortcuts no longer fire behind an open dialog or while a button/row has focus, so Space and Enter activate the focused control only once.

## [0.1.5] — Previous Release

### Fixed
- Empty library, empty playlist and empty search no longer crash rendering (boot no longer aborts).
- The Keyboard Shortcuts dialog now exists and opens from Preferences ▸ Help and `?`; Esc closes dialogs.
- The Preferences modal was missing its closing tag, which left toasts, About, Changelog, Rip CD, the confirm dialog, the mini player and the Keyboard Shortcuts dialog nested inside a hidden modal.
- The full-screen Preferences header now starts below the custom title bar instead of being covered by it.
- Preferences "Apply & Close" now reads the form instead of discarding changes.
- M3U import splits lines correctly and preserves Windows paths.
- Lyrics timestamps support 1–3 fractional digits (.5 / .34 / .345).
- Duplicate visualizer/EQ listeners removed (was running two animation loops).
- File URLs encode `#` and `?`, so those filenames play.
- Play counts log after 20 s of playback; library saves are debounced, atomic and keep a `.bak`; damaged files are quarantined.
- Remote artwork is validated and escaped, and a Content-Security-Policy is in place.
- Seek bar no longer fights progress updates while dragging; the light theme uses light backgrounds.
- Visualizer canvas sizes from its own box, so non-default font zoom no longer blurs or misaligns it.
- The generic close-button handler no longer throws on the Changelog and Welcome ✕ buttons.
- Closing the window hides to the tray; tray ▸ Quit and File ▸ Exit really quit; restored window position is clamped on-screen.
- Title bar menus auto-hide/swap work again.
- Version in the title bar and About comes from package.json.
- Applying preferences updates the track list (album art toggle) without switching views.
- Missing files report "file not found" instead of an unsupported-format error.
- Manual track selection starts immediately; crossfade now applies only to automatic advances.
- Managed Libraries rows no longer print the folder status twice.
- CD ripping detects ffmpeg/ffprobe, shows install guidance and disables Rip when they are missing.
- Search input is debounced and track rows render in a single batch (200 rows: ~183 ms, was ~198–283 ms).

### Added
- ReplayGain normalization (track/album gain + preamp) applied in the audio graph, with saved Audio-tab controls.
- Gapless playback preloads the next file and hands off without a crossfade pause.
- CD ripping (beta): detects the drive, fetches metadata from MusicBrainz and rips to MP3; detection runs on demand instead of every 15 seconds.
- Help moved into Preferences as a tab.
- Drag-to-reorder and resizable track columns with a hover separator.
- Banner image integrated.
- `npm run smoke` — CDP-driven smoke test covering startup, empty states, dialogs, M3U/LRC parsing, ReplayGain, Preferences, metadata, scanning and playback.

## [0.1.4] — Previous Release

### Features & Changes
- Context menus fit within the viewport (no full-width overflow).
- Column customization also reachable from the View menu.
- Hover-to-play overlay on album art in list view.
- Lyrics auto-fetch on track change.
- Title bar displays "AMP (0.1.4)".
- Renamed "Watched Folders" to "Managed Libraries".
- About window with creator credit (Donald Fagerlie) and AI disclaimer.
- Welcome overlay Add Folder now adds to managed libraries.
- Expanded Managed Libraries: per-folder stats, rescan, remove missing, clear library.
- Auto-scan frequency settings (manual/startup/focus/interval).
- Managed Libraries folder health check (OK/Missing badge).
- New tracks badge on recently imported tracks.
- Lyrics tracking highlight & follow with toggle (side panel + preferences).
- Lyrics effect customization (glow/bold/scale/color) and a synced-lyrics-only option.
- Preferences reorganized into tabs (Appearance/Visualizer/Audio/Lyrics/Libraries/Overlays).
- Close / Apply / Apply & Close buttons with an unsaved-changes warning.
- Moved Managed Libraries into the Preferences window.
- Import/export managed libraries list (JSON).
- Per-library auto-scan toggle.

### Fixes
- Fixed view reset on play (artist/album/genre views preserved).
- Fixed random blue dashes around the main window.
- Fixed font selection not applying.
- Fixed online fetch not writing to the track.
- Fixed sort button dropdown misalignment.
- Fixed the managed libraries dialog not listing folders and its close button showing a "?" glyph.
- Fixed repeat-one skip restarting the track.

## [0.1.3] — Previous Release

### Features & Changes
- Polished library views (Albums, Artists, Genres) with track counts and helpful empty states.
- Added "Remove Duplicates" action in the Tools menu.
- Removed the Folders view from the library panel.
- Moved Recently Played, Most Played and Recently Added to automatic playlists (Top 50 each).
- Changed the default background to Aurora.
- Prompt to add a folder on startup when the library is empty.
- Title bar menus auto-hide and stay open while hovering dropdowns.
- Player bar redesigned: info/shuffle/repeat stacked on the left, neutral controls, accent-filled progress bar with dot.
- Watched Folders button accent colored, + button aligned.
- Title bar displays "AMP (0.1.3)".
- Added font family selector in Preferences (9 fonts).
- Mini player scales artwork and auto-hides controls.

### Fixes
- Fixed genre view showing no icons (genres now use representative art or icons).

## [0.1.2] — Previous Release

### Features & Changes
- Renamed "Customize" to "Preferences" (unified naming).
- Preferences organized into sections (Appearance, Visualizer, Audio, Overlays) with better spacing.
- Added more background options (Ocean, Forest, Aurora) plus a custom picture with blur/darken effects.
- Font size (Small/Medium/Large) now actually scales the UI via zoom.
- Mini player now shows album artwork + prev/play/next controls.

### Fixes
- Fixed compact density misalignment (title bar, player bar, side panel, track rows).
- Fixed visualizer auto-hide controls.
- Fixed Aurora/Spectrogram/Plasma visualizers.
- Fixed track list column header sorting.

## [0.1.1] — Previous Release

### Features
- Cross-platform desktop music player (Windows installer/portable, Linux AppImage config).
- Library views: All Tracks, Albums, Artists, Genres, Folders, Favorites, Recently Played, Most Played, Recently Added.
- Grid/list toggle, global search, multi-column sort, customizable visible columns via right-click header (12 available tags).
- Custom playlists + M3U import/export.
- Playlists: added a "Back to Playlists" button inside playlists.
- Watched folders with auto-scan on startup/focus + manual scan.
- Drag-and-drop files/folders into the library.
- Favorites, 0–5 star ratings, play counts, last-played tracking.
- Playback: play/pause, previous/next, shuffle, repeat, skip ±30s, seek, volume, speed (0.5–2x), crossfade (0–12s), sleep timer.
- Queue panel (reorder/remove/clear/shuffle) and mini player mode.
- 10-band equalizer (8 presets, enable/disable).
- 15 fullscreen visualizers with customization (color modes, sensitivity, bars, smoothing, glow).
- Metadata reading + online search (iTunes, Deezer, MusicBrainz) and cover art fetch.
- Manual tag editing (title, artist, album, album artist, year, genre, track, disc).
- Lyrics fetch with synced LRC highlighting; side panels swappable with auto-fetch on tab switch.
- Custom frameless title bar with menus (File/Edit/View/Playback/Tools/Help) and logo.
- Dark/light themes, accent color, 5 backgrounds, density, font size, album art toggle, accent play button.
- Overlays: welcome (first run) and changelog (updates).
- Toast notifications, loading overlay, empty states.
- System tray, global media keys, taskbar progress, window title, window state persistence.
- File associations, single-instance.
- Neutral player controls with optional accent coloring.

### Fixes
- Fixed overlay close button (`.hidden` now `!important`).
- Fixed sort button and "..." (More) button not functioning.
- Fixed watched folders "+" button not wired.
- Fixed plasma visualizer performance (low-res offscreen canvas).
- Fixed Aurora visualizer `ReferenceError: v is not defined`.
- Fixed Spectrogram visualizer scrolling.
- Fixed Add menu dropping down instead of popping up.
- Fixed side panel covering the title bar.
- Fixed track list stacking columns; now horizontal scroll.
- Removed leftover debug code.

## Roadmap

Planned work lives in [ROADMAP.md](ROADMAP.md).

---

## Version History
Releases increment 0.1.x one step at a time; 0.2.0 marks the next major milestone.
- **0.1.7** — Current release
- **0.1.6** — Previous release
- **0.1.5** — Previous release
- **0.1.4**, **0.1.3**, **0.1.2**, **0.1.1** — Earlier releases
