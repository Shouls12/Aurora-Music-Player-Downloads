# Aurora Music Player

A desktop music player for Windows and Linux, made for people who keep their music in folders.

Aurora reads your local library, plays it, and remembers what you listen to. No account, no
telemetry, nothing uploaded anywhere. It started as a personal project and is still one.

![The All Tracks view, with a track playing and albums on the left](images/library.png)

![The Albums view, showing cover art in a grid](images/albums.png)

## Download 0.1.8

- **[Windows installer](https://github.com/Shouls12/Aurora-Music-Player-Downloads/releases/download/v0.1.8/Aurora.Music.Player.Setup.0.1.8.exe)** — installs the app and registers common audio file types
- **[Windows portable](https://github.com/Shouls12/Aurora-Music-Player-Downloads/releases/download/v0.1.8/Aurora.Music.Player.0.1.8.exe)** — a single executable, no install
- **[Linux AppImage](https://github.com/Shouls12/Aurora-Music-Player-Downloads/releases/download/v0.1.8/Aurora.Music.Player-0.1.8.AppImage)** — `chmod +x` it, then run
- [SHA-256 checksums](https://github.com/Shouls12/Aurora-Music-Player-Downloads/releases/download/v0.1.8/SHA256SUMS.txt) · [release manifest](https://github.com/Shouls12/Aurora-Music-Player-Downloads/releases/download/v0.1.8/release-manifest.json) · [release notes](https://github.com/Shouls12/Aurora-Music-Player-Downloads/releases/tag/v0.1.8)

Not sure which Windows file to grab? The installer is the normal choice. The portable build is handy
for a USB stick or a machine where you can't install software.

## What's coming

Library workflows and format depth are next: choose your sidebar sections, automatic Top Artists and
Top Genres lists, batch track info, screen-reader and keyboard work, cue-sheet albums and decoders
for the formats that still need one. The [roadmap](ROADMAP.md) has the plain-language plan.

## What's in it

- All Tracks, Albums, Artists, Genres and Favorites, plus automatic Recently Played and Most Played lists
- Your own playlists with drag-to-reorder, M3U import/export, and smart playlists with rules
- A 10-band equalizer, 18 visualizers, crossfade, gapless playback, ReplayGain and a sleep timer
- Synced lyrics that scroll with the song
- Tag editing straight to MP3, FLAC and Ogg Vorbis files, including cover art
- Watch folders, a duplicate finder, and backup/restore for your library and settings
- Automatic updates for the installed build, with restart-or-later, plus more audio formats imported
  with their titles, artists and cover art
- Dark and light themes, a compact mini player, and global media keys

0.1.8 added automatic updates, wider format import and resizable side panels. The [changelog](CHANGELOG.md) has the details,
and older builds live under
[releases](https://github.com/Shouls12/Aurora-Music-Player-Downloads/releases).

## A couple of honest notes

The Windows builds are unsigned. That's a deliberate choice for a free hobby project, so SmartScreen
will probably say "unknown publisher" the first time you run it. The AppImage is built and tested in
an isolated Linux environment.

Some formats import but will not play until a decoder ships. WMA, APE, WavPack and DSD files are
listed with their metadata and marked in the track list; pressing play explains why. AAC/M4A, ALAC,
WAV, AIFF, Opus, MP3, FLAC and Ogg all play directly.

## Checking your download

If you'd like to confirm the file arrived intact, compare it against `SHA256SUMS.txt`:

```bash
sha256sum -c SHA256SUMS.txt
```

On Windows PowerShell:

```powershell
Get-FileHash .\Aurora.Music.Player.Setup.0.1.8.exe -Algorithm SHA256
```

---

Aurora is a free hobby project. This repository only holds release builds; the source stays private.
The [roadmap](ROADMAP.md) and [changelog](CHANGELOG.md) are public. Built with Electron.
