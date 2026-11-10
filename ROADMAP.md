# The future of Aurora

Aurora is built in small steps, and this is the order those steps are planned in. There are no
dates. It is a hobby project, and a bug that could lose someone's library always comes before a new
feature.

## Where Aurora is today

The current release is **0.1.8**. Aurora plays a local music library on Windows and Linux: All
Tracks, Albums, Artists, Genres and Favorites, your own playlists and smart playlists, a 10-band
equalizer, 18 visualizers, synced lyrics, ReplayGain, gapless playback, tag writing to MP3, FLAC and
Ogg Vorbis, folder watching, duplicate finding, backup/restore and automatic updates. AAC/M4A, ALAC,
WAV, AIFF, Opus, WMA, APE, WavPack and DSD files import with their metadata and artwork.

## Coming next — 0.1.9

**A sidebar that fits the way you listen.** Choose which sections appear, with a safe fallback when
the current view is hidden, and one shared list that keeps menus, shortcuts and the sidebar in step.

**Playlists that know what you play.** Automatic Top Artists and Top Genres lists, built from your
listening rather than a rule you have to write.

**Faster metadata work.** Batch Track Info walks through every selected track one after another, and
one-click lookup can fill in a whole album with a clear warning that automatic matching can pick the
wrong release.

**Deeper format support.** Cue-sheet albums become individual tracks, and WMA, APE, WavPack and DSD
get a decoder-backed playback path. Formats without a decoder keep the plain explanation they have
today.

**The quality gates.** Screen-reader labels, high contrast, complete keyboard navigation, faster
startup for very large libraries, and more visualizers and equalizer presets.

## After that — 0.1.10

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

## On your phone — 0.3.0

Aurora on Android will start as a companion, not a second library. Pair your phone with the desktop
over your home network, then use it to browse what is playing, search the library, manage the queue
and control playback and volume.

The app will be a signed APK you install directly from the releases page, with the same checksums and
release notes as the desktop builds. There is no Play Store release planned yet, and the phone will
not store or scan your music on its own — that would be a separate app with its own plan.

## What Aurora won't do

- No ads, no tracking and no account requirement.
- No DRM circumvention.
- No ripping or downloading from streaming services.
- Windows code signing is out of scope for a free hobby project.

## How this list changes

The order can move. Data safety and bugs come first, and a release only ships when its checks pass.
The [changelog](CHANGELOG.md) records what has actually shipped, and
[releases](https://github.com/Shouls12/Aurora-Music-Player-Downloads/releases) has the builds.
