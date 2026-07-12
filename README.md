# Marquee — a custom video player

A cinema-styled video player: drag-and-drop playlist, custom seek bar with **live thumbnail
scrubbing**, an **ambient glow** that lights the screen with colors pulled from the video itself,
picture-look filters, pinch/scroll **zoom & pan**, resume-where-you-left-off, subtitles (.vtt / .srt),
A–B loop, sleep timer, playback speed, Picture-in-Picture, fullscreen, keyboard shortcuts, and
mobile gestures (double-tap to skip, swipe for brightness/volume). Built as a single web app that
runs in any modern browser on laptop, Android, or iPhone.

## Use it right now, no setup
Just open `index.html` by double-clicking it. Everything works locally — no install needed.
Drag a video file onto it, or click **Open Files**.

## Install it as an app (Android / desktop / iPhone)
Browsers only allow installing a site as an app ("PWA") when it's served over HTTPS, not
when opened as a local file. So to get the home-screen icon / app-window experience:

1. Upload this whole folder (`index.html`, `manifest.json`, `sw.js`, `icon.svg`) to any free static
   host — e.g. **GitHub Pages**, **Netlify Drop** (netlify.com/drop — just drag the folder in), or
   **Vercel**.
2. Open the live URL it gives you:
   - **Android / Chrome desktop**: you'll see an "Install" icon in the address bar, or a banner —
     tap it to add Marquee as an app.
   - **iPhone / Safari**: tap the Share icon → **Add to Home Screen**. It'll launch full-screen like
     a native app.
3. From then on it opens like any installed app, and the service worker lets the app shell load
   even with a flaky connection (the videos themselves still need to be local files or a reachable
   URL — the app doesn't store movies for you).

## What's new in this version

- **Ambient glow** — a soft, blurred halo behind the picture that shifts color with whatever's on
  screen, like a bias light for your browser. Toggle it in Settings.
- **Picture-look filters** — Normal, Vivid, Warm, Cool, Noir (black & white), and Theater presets,
  applied live via the palette icon in the control bar.
- **Zoom & pan** — pinch on mobile or scroll the wheel on desktop to zoom into the frame (up to 3×),
  then drag to pan. The aspect button cycles Fit / Fill / Stretch.
- **Live scrub thumbnails** — hover (or drag) the seek bar to see an actual frame preview of that
  point in the video, not just a time stamp.
- **Resume where you left off** — playback position is now remembered per file (stored locally on
  your device only), with a "Resume" badge on the playlist thumbnail and a toast when it jumps you
  back in.
- **A–B loop** — mark two points and loop that section endlessly. Handy for practicing a scene, a
  song, or a language clip.
- **Sleep timer** — 15/30/45/60-minute options that pause playback automatically, with a countdown
  in the top bar.
- **Subtitle styling** — adjust caption size, background opacity, and text color from Settings.
- **Playlist upgrades** — search box, shuffle, repeat, drag-to-reorder, and watched/resume badges.
- **Accent color themes** — five color palettes (Gold, Emerald, Azure, Rose, Silver) for the whole
  interface.
- **Gestures** — double-tap the left/right edge to skip ±10s, or swipe up/down on the left half for
  brightness and the right half for volume, the way most mobile cinema apps work.
- **Playback stats overlay** — press `I` or flip it on in Settings to see resolution, buffered
  seconds, dropped frames, and current zoom.
- **Keyboard shortcuts help** — press `?` any time for the full list.
- **A short curtain-opening animation** when a video starts, because it's a theater.

## Format support — please read
This is a real limit of *any* browser-based player, not just this one: a website can only decode
the video formats your device's browser has a built-in decoder for. It cannot bundle its own
codec library the way VLC does.

- **Reliable everywhere:** MP4 (H.264/AAC), WebM (VP9), MOV (H.264)
- **Usually fine:** WebM (AV1) on newer browsers
- **Often unsupported:** MKV with certain codecs, AVI, WMV, RMVB, older DivX/Xvid files

If a file won't play, the app will tell you it's a format/codec issue rather than failing silently.
For those stubborn old files, VLC itself (the actual desktop app) remains the safer bet, since it
ships its own decoders.

## Keyboard shortcuts (desktop)
- `Space` / `K` — play/pause
- `←` / `→` — seek 5s · `J` / `L` — seek 10s
- `,` / `.` — step one frame while paused
- `0`–`9` — jump to 0%–90% of the video
- `↑` / `↓` — volume
- `M` — mute
- `F` — fullscreen
- `<` / `>` — playback speed
- `+` / `-` — zoom in/out
- `A` / `B` — set A–B loop points
- `I` — toggle playback stats
- `?` — shortcuts help

## Mobile gestures
- Tap center — play/pause
- Double-tap left edge — back 10s · double-tap right edge — forward 10s
- Swipe up/down on the left half — brightness · right half — volume
- Pinch — zoom, then drag to pan while zoomed in

## Known limitations
- Subtitles support `.vtt` natively; `.srt` files are auto-converted on load.
- Streaming URLs must allow cross-origin playback (some sites block embedding).
- Resume positions, settings, and theme choices are stored only in your browser's local storage on
  this device — they aren't synced anywhere.
