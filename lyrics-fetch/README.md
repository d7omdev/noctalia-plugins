# lyric-fetch Plugin

Uses MPRIS data to fetch lyrics from `lrclib.net`, and plays shows them in the bar.

## Features

- Adjust scroll speed of lyrics
- Adapt scroll speed to the length of the line
- Change font and font size

- Add the Music Search bar widget to open a dedicated panel in one click
- The panel exposes search, playback controls, saved tracks, and queue management without going through the launcher
- The launcher provider still exposes the full command surface when you want advanced flows like `playlist:`, `tag:`, or `edit:`

Search results and saved tracks expose inline actions for queueing, saving, downloading, metadata edits, tags, and playlists. Queue controls are now part of the music-search plugin, so the old standalone `queue` plugin should be treated as legacy.

The internal plugin ID remains `music` for IPC compatibility.

## IPC usage

```bash
qs -c noctalia-shell ipc call plugin:music launcher
qs -c noctalia-shell ipc call plugin:music panel
qs -c noctalia-shell ipc call plugin:music play "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
qs -c noctalia-shell ipc call plugin:music save "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
qs -c noctalia-shell ipc call plugin:music seek 90
qs -c noctalia-shell ipc call plugin:music stop
```

## Data files

- By default, runtime data lives under `~/.cache/noctalia/plugins/music-search/`
- `~/.cache/noctalia/plugins/music-search/library.json` stores saved tracks and playback stats
- `~/.cache/noctalia/plugins/music-search/playlists.json` stores playlists
- `~/.cache/noctalia/plugins/music-search/queue.json` stores the built-in persistent queue
- `~/.cache/noctalia/plugins/music-search/state.json` stores current playback state
- `~/.cache/noctalia/plugins/music-search/settings.json` stores local user state
- Set `MUSIC_CACHE_DIR` to override the default cache directory
