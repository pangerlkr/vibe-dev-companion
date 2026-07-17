# Vibe Dev Companion

> An Electron-based AI developer companion — merges VibeDroid + custom enhancements into a unified, dynamically functional desktop app.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Electron](https://img.shields.io/badge/electron-43.x-47848f.svg)
![Version](https://img.shields.io/badge/version-2.0.0-brightgreen.svg)

---

## What is this?

**Vibe Dev Companion** is a frameless Electron desktop app that wraps your local dev server (e.g. `http://localhost:5173`) inside a sleek phone-frame UI — letting you preview, test, and interact with your web app just like a real mobile device, with AI-powered screen capture running in the background.

This repo is a **full merge** of:
- [`leethongs/vipedroid`](https://github.com/leethongs/vipedroid) — original concept
- [`pangerlkr/vipedroid`](https://github.com/pangerlkr/vipedroid) — enhanced fork with IPC, prefs & UI overhaul

All improvements are consolidated here as a clean, standalone project.

---

## Features

### Core
- Phone-frame viewport (412 x 868px) with rounded corners and camera hole
- Frameless, transparent Electron window
- Always-on-top mode (pinnable)
- Connect to any local dev server by URL
- Enter key + button to navigate

### AI Capture
- Periodic screen captures saved as `live_feed.png` in app directory
- Toggle AI capture on/off from the title bar
- Open the live feed directly in your system image viewer

### Persistent Preferences
- Last visited URL remembered across sessions
- AI capture state and always-on-top preference saved to `vibedroid-prefs.json`
- URL history logged to `url-history.log`

### UI / UX
- Frosted-glass title bar with gradient app name
- 6 control buttons: Pin, AI toggle, Feed viewer, History, Minimize, Close
- URL history dropdown (up to 20 entries, click to navigate, clearable)
- AI status badge (bottom-right, live ON/OFF indicator)
- Animated splash screen with conic-gradient orb, 7-step progress bar, and "AI Ready" badge

---

## Getting Started

### Prerequisites
- [Node.js](https://nodejs.org/) v18+
- npm

### Install

```bash
git clone https://github.com/pangerlkr/vibe-dev-companion.git
cd vibe-dev-companion
npm install
```

### Run

```bash
npm start
```

Optionally pass a URL as a startup argument:

```bash
npm start -- http://localhost:3000
```

---

## Project Structure

```
vibe-dev-companion/
├── index.js        # Main process: window, IPC handlers, AI capture, prefs
├── index.html      # Renderer: title bar, phone frame, history panel, AI badge
├── style.css       # All component styles (frosted glass, badges, phone frame)
├── splash.html     # Animated loading screen shown on startup
├── package.json
└── .gitignore
```

---

## IPC Channels

| Channel | Direction | Description |
|---|---|---|
| `url-navigate` | renderer → main | Navigate to URL, save to prefs & history log |
| `set-always-on-top` | renderer → main | Toggle window always-on-top |
| `minimize-window` | renderer → main | Minimize the app window |
| `close-window` | renderer → main | Close the app window |
| `capture-toggle` | renderer → main | Enable/disable AI screen capture |
| `open-feed` | renderer → main | Open `live_feed.png` in system viewer |

---

## License

MIT © [pangerlkr](https://github.com/pangerlkr)

---

> Built from open-source contributions to [`leethongs/vipedroid`](https://github.com/leethongs/vipedroid). PRs welcome.
