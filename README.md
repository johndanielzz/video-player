# Marquee — a custom video player

A cinema-styled video player: drag-and-drop playlist, custom seek bar, subtitles (.vtt / .srt),
playback speed, Picture-in-Picture, fullscreen, keyboard shortcuts, and mobile double-tap-to-skip
gestures. Built as a single web app that runs in any modern browser on laptop, Android, or iPhone.

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
- `←` / `→` — seek 5s
- `↑` / `↓` — volume
- `M` — mute
- `F` — fullscreen
- `<` / `>` — playback speed

## Mobile gestures
- Tap center — play/pause
- Double-tap left edge — back 10s
- Double-tap right edge — forward 10s

## Known limitations
- Playback position isn't remembered after closing the app (kept in-memory only, by design).
- Subtitles support `.vtt` natively; `.srt` files are auto-converted on load.
- Streaming URLs must allow cross-origin playback (some sites block embedding).
