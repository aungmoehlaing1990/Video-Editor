# CapCut Pro — Offline Video Editor

A single-file, fully offline video editor inspired by CapCut. No server, no API key,
no install — just open `capcut-pro.html` in any modern browser (Chrome/Edge/Firefox/
Brave). Everything runs locally in your browser; your media never leaves your machine.

## Features
- **Import** video, image, and audio files (multi-select).
- **Multi-track timeline** — Video, Image, Text, Audio tracks.
- **Drag & drop** clips on the timeline; **drag the edges** to trim (in/out points).
- **Split** a clip at the playhead (double-click a clip, or the Split button).
- **Snapping** to clip edges and the playhead.
- **Canvas preview** with live compositing of all layers.
- **Text overlays** with font size, color, stroke, shadow, background, alignment,
  and entrance animations (fade / pop / slide / typewriter).
- **Filters** — B&W, Warm, Cool, Vivid, Fade, Cinematic, Vintage, Invert, Blur.
- **Transform** — position (X/Y), scale, rotate, opacity, fit mode (cover/contain/stretch).
- **Speed** control (0.25×–4×) and **volume** control per clip.
- **Playback** engine with smooth master clock + media-element sync.
- **Save / Open** project to browser localStorage.
- **Export** to **WebM** (VP8/VP9 + Opus) at 540p/720p/1080p, 24/30/60 fps, with a
  real mixed audio track (video audio + audio clips) — all rendered in-browser via
  `canvas.captureStream()` + `MediaRecorder` + Web Audio API.
- **Mobile-responsive** UI (sidebar collapses; larger touch targets).

## How to use
1. Open the file. Click **+ Video / + Image / + Audio** to import. Clips appear in the
   Media bin on the left.
2. Click a media clip to drop it onto the timeline (it lands at the end / playhead).
3. Select a clip to edit it in the right-hand **Properties** panel.
4. Use the timeline: drag to move, drag edges to trim, double-click to split.
5. Press **Space** to play/pause. Use the **Export** button to render a WebM.

### Shortcuts
- `Space` — play / pause
- `Delete` / `Backspace` — delete selected clip
- `Ctrl/Cmd + S` — save project

## Notes & limits
- Export produces **WebM** (the only container browsers can encode without a server).
  Convert to MP4 with ffmpeg if needed: `ffmpeg -i clip.webm clip.mp4`.
- Object URLs are session-scoped: reloaded projects keep clip settings but you must
  re-import the original files (browsers cannot persist local file paths for privacy).
- Very large source videos may need trimming before import on low-memory devices.
- Audio via Web Audio requires the page be served from `file://` or `https://`
  (standard browser security). Double-clicking the file works fine.

## Verifying the build
`node verify.js capcut-pro.html` runs syntax + pure-logic tests (no DOM needed).

## Privacy
100% client-side. No telemetry, no network calls, no uploads.
