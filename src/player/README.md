# Playback Core

libmpv integration, playback controllers, IPC, options, and media-engine coordination.

## Scope

Keep mpv access serialized through the established player abstractions and avoid competing state writers in QML.

## Online Quality

The YouTube Quality selector in Preferences and the Solar 4K menu in YouTube
Search share `SettingsManager.youtubeQuality`. Automatic requests the best
available video and audio; resolution presets prefer streams at or below
144p through 2160p, with a combined video/audio fallback. Unknown-height formats
remain eligible. If every known-height format exceeds the limit, choose a higher
preset or Automatic.

`PlaybackController` applies the preference to mpv's `ytdl-format` before loading,
including renderer-delayed startup and docked videos. Changes affect the next URL
opened, not already selected streams, and leave local-file playback unchanged.
The setting applies to other sites handled by mpv's yt-dlp hook as well.

## Related

- [Parent directory](../README.md)
- [Project overview](../../README.md)
- [License](../../LICENSE.md)
