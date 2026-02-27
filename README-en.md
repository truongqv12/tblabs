<p align="center">
  <h1 align="center">🧪 TP-LABS Desktop App</h1>
  <p align="center">
    <strong>AI Image & Video Generation Workstation for Windows</strong>
  </p>
  <p align="center">
    Automate Google Labs workflows — generate images, create videos, manage accounts — all from a single desktop app.
  </p>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/platform-Windows-blue?style=flat-square&logo=windows" alt="Windows">
  <img src="https://img.shields.io/badge/python-3.12-green?style=flat-square&logo=python&logoColor=white" alt="Python 3.12">
  <img src="https://img.shields.io/badge/UI-PySide6%20(Qt)-41CD52?style=flat-square&logo=qt&logoColor=white" alt="PySide6">
  <img src="https://img.shields.io/badge/license-proprietary-lightgrey?style=flat-square" alt="License">
</p>

---

## ✨ Features

### 🖼️ Image Generation
- **Whisk Service** — async image generation with retry and validation
- **Flow Service** — image generation with reCAPTCHA token flow and reference image upload
- **Character Image Creator** — character-consistent generation with `@name` reference syntax
- **Batch Processing** — bounded concurrency for multiple prompts with semaphore-based throttling

### 🎬 Video Generation
- **4 Generation Modes:**
  - `Text → Video` — generate video from text prompts
  - `Reference → Video` — use reference images to guide generation
  - `Start Image → Video` — animate a starting image
  - `Frame → Video` — frame-by-frame video generation
- **Reference Video Creator** — batch mapping from image folder to prompts
- **Full Lifecycle** — submit → poll → download → save, fully automated
- **FFmpeg Integration** — video concatenation and post-processing

### 👤 Account & Session Management
- Playwright-based browser automation with stealth mode
- Multi-account support with persistent sessions
- Automatic session recovery and cookie management

### 💳 Membership & Subscription
- Google Token / License Key authentication
- Membership tier display and purchase flow
- Real-time order status polling with dialog-scoped lifecycle
- Subscription sync from server on startup

---

## 🚀 Getting Started

### Download Pre-built Release

1. Go to the [**Releases**](../../releases) page
2. Download the latest `.zip` archive
3. Extract to any folder
4. Run `tplab.exe`

> **No Python installation required** — the release is a fully standalone executable with all dependencies bundled.

### System Requirements

| Requirement | Details |
|-------------|---------|
| **OS** | Windows 10/11 (64-bit) |
| **RAM** | 4 GB minimum, 8 GB recommended |
| **Disk** | ~500 MB for the app + browser |
| **Network** | Internet connection required |

---

## 📸 Screenshots

> _Screenshots coming soon_

<!-- 
Uncomment and update paths when screenshots are available:
| Feature | Preview |
|---------|---------|
| Image Creator | ![Image Creator](screenshots/image-creator.png) |
| Video Creator | ![Video Creator](screenshots/video-creator.png) |
| Account Manager | ![Account Manager](screenshots/account-manager.png) |
-->

---

## 🏗️ Architecture Overview

```
tplab/
├── tplab.exe              # Main executable
├── playwright/            # Bundled Chromium browser + driver
│   └── driver/
│       └── package/
│           └── .local-browsers/
├── ffmpeg/                # Bundled FFmpeg for video processing
├── src/
│   └── ui/
│       └── styles/        # QSS theme files (Dark theme)
└── [runtime dependencies]
```

The app is built with:

| Component | Technology |
|-----------|-----------|
| **UI Framework** | PySide6 (Qt for Python) |
| **Browser Engine** | Playwright + Chromium |
| **HTTP Client** | httpx (async) |
| **Database** | SQLite (local task persistence) |
| **Data Models** | Pydantic v2 |
| **Video Processing** | FFmpeg |
| **Compiler** | Nuitka (Python → native executable) |

---

## 🎨 Design

The app features a **modern dark theme** inspired by Tailwind Slate + Blue palette:

- 🌑 Dark backgrounds (`#0f172a` / `#1e293b`) for reduced eye strain
- 🔵 Blue accent colors (`#3b82f6`) for interactive elements
- ✅ WCAG AA+ compliant text contrast
- 🎯 Smooth transitions and hover effects

---

## ⚡ Performance

- **Bounded Concurrency** — semaphore-based throttling prevents API rate limiting
- **Non-blocking UI** — all long-running operations run on async worker threads
- **Smart Retries** — bounded retry policies with exponential backoff
- **Session Persistence** — SQLite-backed task state survives app restarts

---

## 🔐 Security

- Auth tokens stored securely via `CustomerTokenStore`
- No sensitive data logged
- Isolated customer auth domain (separate from browser sessions)
- Token refresh with single-retry policy

---

## 📋 Changelog

See [CHANGELOG](docs/project-changelog.md) for version history and release notes.

---

## 🤝 Support

If you encounter any issues or have questions:

- 📧 Contact the development team
- 🐛 Open an issue in this repository

---

## 📄 License

This software is proprietary. All rights reserved.

---

<p align="center">
  <sub>Built with ❤️ using Python, PySide6, and Playwright</sub>
</p>
