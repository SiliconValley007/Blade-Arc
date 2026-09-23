# Blade Arc

A production-ready, Fruit Ninja-style arcade slicer. Swipe, keyboard, or gamepad to cut fruit, chain combos, dodge bombs, and chase a high score.

No builds. No dependencies. Open `index.html` and play.

## Play

Open `index.html` in any modern browser, or host the folder on GitHub Pages.

## Controls

### Pointer (laptop, PC, phone, tablet)
- **Mouse drag** or **Touch swipe** — slice along the path (the blade is the path)
- **II button** — pause
- **Esc** or **P** — pause / resume

### Keyboard (desktop, laptop, TV browser)
- **Arrows** or **WASD** — move; the path is the blade (same as a swipe)
- **Space**, **Enter**, **Z**, or **X** — slice the nearest fruit
- **Enter** / **Space** — Play on title, Restart on game over

### Gamepad (console-style controllers, some TVs)
- **Left stick** or **D-pad** — move; the path is the blade
- **A / RT / RB** — slice the nearest fruit
- **Start / Select** — pause / resume
- **D-pad + A** — move and confirm menus

### Screen reader
- **Slice** button (visible on keyboard focus) cuts the nearest fruit
- Live region announces score, lives, pause, and game over

### Mobile and tablet
- Portrait and landscape supported
- Safe-area padding for notches and home indicators
- Viewport tracks `visualViewport` width, height, and `offsetTop` / `offsetLeft` so iOS URL-bar changes keep slice input aligned with the canvas
- Overscroll / pull-to-refresh blocked during play
- 16px left/right edge guards plus a double `history.pushState` trap on every screen so Back stays in-game (title, pause, play, game over)
- Pause, Game Over, and Title overlays use `touch-action: pan-y` and document `touchmove` is not cancelled unless the run is live, so landscape menus scroll
- Menu buttons stay at least 48px tall in landscape

Pause also triggers automatically when the tab is hidden. Desktop additionally pauses on window blur.

## Features

- Physics-based fruit arcs with gravity and rotation
- Continuous swipe tracking (mouse and multi-touch)
- Keyboard, gamepad, and Slice-button play use the same blade path as a swipe
- Line-segment vs circle slice detection with generous hitboxes
- Combo multiplier with on-slice score pops
- Three-life miss penalty; bombs end the run if sliced
- Progressive difficulty (spawn rate, group throws, bomb chance)
- Fruit split halves, juice particles, and a fading blade ribbon
- Web Audio API SFX (slice, miss, combo, bomb) — no audio files
- Pause menu: Resume, Restart, Sound toggle, Title
- High score persisted in `localStorage`
- Object pooling, 60 FPS `requestAnimationFrame` loop
- Fully responsive fullscreen canvas
- Coalesced pointer samples plus path interpolation (fast swipes still hit)
- Touch-event fallback for older iOS / WebViews
- Safe `localStorage` (Safari private mode will not crash; high score is in-memory only)
- Bundled Open Sans Bold (`fonts/OpenSans-Bold.ttf`) so UI type matches across OS
- Fixed 1/60s physics step (same motion on 60 / 90 / 120 Hz panels)
- Canvas DPR up to 3, with an 80M pixel budget so 4K stays at native sharpness
- Combo HUD drops below the score on narrow phones so it never overlaps
- Canvas 2D / no-JS fallback messages instead of a blank screen
- Favicon, Apple touch icon, and web app manifest for home-screen install

## Pause menu

| Action | What it does |
| --- | --- |
| Resume | Continue the current run |
| Restart | New run from score 0 |
| Sound | Toggle procedural SFX |
| Title | Return to the title screen |

## Tech stack

- Vanilla JavaScript (ES6)
- HTML5 Canvas
- Web Audio API
- CSS overlay HUD / menus
- Zero runtime CDNs; local Open Sans Bold (SIL OFL) in `fonts/`

All fruit, particles, trails, and sounds are generated at runtime.

## Deploy on GitHub Pages

1. Create a GitHub repository.
2. Push `index.html`, `fonts/`, icons, `manifest.json`, `.nojekyll`, `LICENSE`, and this `README.md` to the repository root.
3. Push to `main`.
4. Open **Settings → Pages**.
5. Set source to **Deploy from a branch**, branch `main`, folder `/ (root)`.
6. Save. The game is live at `https://<user>.github.io/<repo>/`.

Local play: double-click `index.html` or serve the folder with any static file server.

## Browser support

Chrome, Firefox, Safari, Edge, and current iOS / Android / TV browsers. Requires Canvas 2D. Audio uses Web Audio when available. Gamepad API is used when a controller is connected.

## License

MIT. See `LICENSE`.
