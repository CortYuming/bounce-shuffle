# Bounce Shuffle

Shuffle-play the newest export of every track in a local folder. Built for listening back to work in progress: point it at the folder your DAW bounces into and it plays only the latest version of each track, in random order, picking up new exports as they land.

## demo site

https://cortyuming.github.io/bounce-shuffle/

## Requirements

A desktop Chromium browser (Chrome or Edge). The page reads a local folder through the File System Access API, which other browsers do not offer.

## How it works

- **Choose folder** once. The browser remembers it; on later visits the list is there straight away. If access has lapsed, **Resume access** asks again with one click, and until then the last list is shown greyed out
- Files are grouped into tracks by the first two `_`-separated parts of the name, and the most recently modified file in each group is the one that plays. With `20240105_groove_v3.aif`, `20240105_groove_v4.aif` and `20240105_groove_v4b.aif`, the track is `20240105_groove` and whichever of the three was written last plays
- Only files directly inside the folder are read; subfolders are ignored, so an `old/` folder keeps outtakes out of the list
- One round plays every track once in shuffled order and then stops. The list keeps that order, with played tracks dimmed and ▶ on the current one
- The folder is read again before each track, so a new export joins the round at a random point among the tracks not yet played
- Nothing is uploaded. Files are read and played in the browser

Supported formats: AIFF, WAV, MP3, M4A/AAC, FLAC, Ogg, Opus. Chrome does not play AIFF, so uncompressed AIFF is turned into WAV in the page before playback.

## Controls

| Control | Key | Action |
|---------|-----|--------|
| Play / pause | `Space` | Pauses or resumes. After a finished round, starts a new one |
| Next | `N` | Moves to the next track. Playing carries on playing; stopped stays stopped with the next track loaded |
| Reshuffle | `R` | Shuffles a new order. A playing track moves to the top and keeps playing; otherwise the first track of the new order is loaded |
| Seek bar | | Jump within the track |
| Speaker / slider | | Mute and volume. The volume is remembered |

Clicking a track in the list plays it.

## Install as an app

Chrome's install button in the address bar adds it as an app with its own window. An installed app keeps folder access without asking again.

## Credits

Icons: play, pause, skip next and volume from [Material Icons](https://github.com/google/material-design-icons) (Apache-2.0); shuffle from [Lucide](https://lucide.dev) (ISC).
