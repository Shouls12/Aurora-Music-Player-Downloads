# Aurora Music Player — what's new

Release notes for Aurora Music Player. Downloads live on the
[latest release](https://github.com/Shouls12/Aurora-Music-Player-Downloads/releases/latest), and
older builds are under [all releases](https://github.com/Shouls12/Aurora-Music-Player-Downloads/releases).

## 0.1.8

### New
- **Aurora updates itself.** The installed Windows build checks for a new version at startup,
  downloads it in the background and asks whether to restart now or later. Portable and AppImage
  builds keep the download link, because replacing a running file is not safe.
- **More of your library opens.** AAC/M4A, ALAC, WAV, AIFF, Opus, WMA, APE, WavPack and DSD files
  now import with their titles, artists and cover art. A file your system cannot decode is marked
  in the list and explains itself when you press play, instead of failing quietly.

### Improved
- **More room for your music.** Drag the edge of the library sidebar or the Queue/Lyrics panel to resize either one. Aurora remembers the widths, and the main view narrows instead of hiding behind the panel. The keyboard can resize a focused divider, and double-clicking resets it.
- Your chosen typeface now carries through the whole app, including buttons and form controls.
- WAV and AIFF files show their real length straight away, so the seek bar is ready before you
  press play.
- Track Info keeps you on the album or artist you were editing after you save, and its window stays
  one size while cover art and matches load.
- The bar that appears when you select several tracks now names them, not just how many there are.
- "Reveal in Explorer" is now **Open in folder**, which reads the same on every platform.
- The Linux tray icon appears properly, and the Linux download no longer carries Windows-only files.

### Fixed
- A collection opens at its first track instead of partway down the list.
- Rows stop looking selected once the selection is cleared.
- Windows builds stay unsigned, as before; SmartScreen may mention an unknown publisher on first run.

## 0.1.7

### New
- **Save your edits into the file.** Track Info can now write the title, artist, album, year,
  genre and cover art back into MP3, FLAC and Ogg Vorbis files. If you would rather leave your
  files untouched, switch it off under Preferences ▸ Backup & Data.
- **Smart playlists.** Build a playlist from rules — genre, year, rating, play count, favorite
  and more — and it keeps itself up to date as your library changes.

### Improved
- **A quieter title bar.** The top menus are gone. Preferences now sits in the sidebar next to
  Managed Libraries, and nothing was lost: playlist import and export are in Backup & Data, the
  sleep timer is in Audio, and the mini player is in Appearance.
- **Notifications you can actually read.** The "metadata ready — save to apply" message now stays
  above open windows, and in-app notifications can be switched off under Preferences ▸ Appearance.

### Fixed
- Pausing no longer leaves the Windows taskbar progress bar stuck.
- Dragging files onto the window works again.
- Opening an audio file while the app is still starting no longer loses it.
- The Keyboard Shortcuts window puts the cursor inside it when it opens.

## 0.1.6

### New
- **Duplicate Finder**, under Preferences ▸ Help. It looks for tracks that match on title, artist,
  album and length, suggests the best copy to keep, and removes library entries by default. There
  is an explicit option to delete files from disk, and it reports any file it could not remove.
- **Backup and restore** for your settings, playlists and library index. Every restore saves a
  snapshot of the current data first.
- **Multi-select** in the track list with Ctrl/Cmd-click and Shift-click, plus a bar to favorite,
  rate, add to a playlist or remove several tracks at once.
- **Appearance presets and quick accent colors**, a startup view and a sidebar width setting.

### Improved
- Playlists and album, artist, genre and folder pages were redesigned with cover art, Play and
  Shuffle actions, and a breadcrumb back to where you came from.
- Large libraries scroll smoothly: only the rows on screen are built, so a 20,000-track collection
  stays responsive.
- Loading placeholders and progress with cancel for scans and imports.
- Typed notifications with hover-pause, a sleep-timer chip you can cancel, and a **Minimize to
  system tray** preference.
- A compact 360 × 200 mini player, a visualizer stage with 18 modes and per-mode colors, a
  virtualized queue with drag-to-reorder, and click-to-seek lyrics.

### Fixed
- The Keyboard Shortcuts window opens and closes reliably.
- The Folders sidebar item that duplicated Managed Libraries is gone; folder tracks open from a
  Managed Libraries row.
- Folder rows are de-duplicated, so the same path is no longer listed twice.
- Layout, theming, playlist search, grid spacing and M3U import fixes across the app.

## Earlier versions (0.1.1 – 0.1.5)

The first releases built the foundation: library views with search, sorting and custom columns;
custom playlists with M3U import and export; watched folders with automatic scanning; favorites,
ratings and play counts; the queue, mini player, 10-band equalizer and visualizers; synced lyrics;
online metadata and cover art; manual tag editing; dark and light themes with accent colors and
backgrounds; a frameless title bar; system tray support, global media keys and file associations;
ReplayGain, gapless playback and CD ripping; and Managed Libraries with per-folder stats, health
checks, scan schedules and JSON import/export.

---

Aurora is a free hobby project. This repository only holds release builds; the source, issue notes
and roadmap stay in the private repository. Windows builds are unsigned, so SmartScreen may warn on
first launch.
