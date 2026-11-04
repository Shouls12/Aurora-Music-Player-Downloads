# The future of Aurora

Aurora is built in small steps, and this is the order those steps are planned in. There are no
dates. It is a hobby project, and a bug that could lose someone's library always comes before a new
feature.

## Where Aurora is today

The current release is **0.1.7**. Aurora plays a local music library on Windows and Linux: All
Tracks, Albums, Artists, Genres and Favorites, your own playlists and smart playlists, a 10-band
equalizer, 18 visualizers, synced lyrics, ReplayGain, gapless playback, tag writing to MP3, FLAC and
Ogg Vorbis, folder watching, duplicate finding and backup/restore.

## Coming next — 0.1.8

**Updates that come to you.** Aurora will check for a new version and offer to install it, with the
release notes in front of you. The installer can update in place; portable builds and the AppImage
keep a manual download, because replacing those files while they run is not safe.

**The formats your library actually contains.** AAC/M4A, ALAC, WAV and AIFF, Opus, WMA, APE,
WavPack, DSD and cue-sheet albums, with metadata and artwork read for each one. When a file cannot
be played, Aurora will say so plainly instead of failing quietly.

Windows builds stay unsigned. That is a deliberate choice for a free project, so SmartScreen will
keep warning on first run.

## After that — 0.1.9

- Choose which sections appear in the sidebar, with a safe fallback if the current view is hidden
- Automatic **Top Artists** and **Top Genres** playlists built from what you actually listen to
- **Batch Track Info**: work through metadata for every selected track, one after another
- One-click metadata lookup, with a clear warning that automatic matching can pick the wrong release
- Screen-reader labels, high contrast and complete keyboard navigation
- Faster startup and artwork handling for very large libraries
- More visualizers and equalizer presets

## Later — 0.1.10

**Listening beyond your own files**

- Podcasts: subscriptions, episode lists, resume where you left off, and a download or stream choice
- Radio: a station directory or a direct stream link, with now-playing information and reconnect
  handling
- Play audio from a URL and keep it in your library like any other track
- Import your Spotify library's names and playlists, then match them to files you own. Aurora will
  not extract audio from Spotify, YouTube or any other service.

**Smaller comforts**

- Last.fm scrobbling and Discord Rich Presence
- A desktop lyrics overlay and an always-on-top mini player
- CD burning, for those who still use them

## The bigger picture — 0.2.0

Aurora 0.2.0 is the platform milestone: a plugin system, macOS support, a phone remote, community
translations and optional cloud sync. After that, 0.2.1 is the video candidate — local video and
direct links playing on the existing visualizer stage, without changing how audio-only use works.

## What Aurora won't do

- No ads, no tracking and no account requirement.
- No DRM circumvention.
- No ripping or downloading from streaming services.
- Windows code signing is out of scope for a free hobby project.

## How this list changes

The order can move. Data safety and bugs come first, and a release only ships when its checks pass.
The [changelog](CHANGELOG.md) records what has actually shipped, and
[releases](https://github.com/Shouls12/Aurora-Music-Player-Downloads/releases) has the builds.
