<p align="center">
  <img src="assets/logo.png" alt="TP-LABS Logo" width="120">
</p>

<h1 align="center">🧪 TP-LABS Desktop App</h1>

<p align="center">
  <strong>Batch AI Image & Video Generation — Fully Automated on Windows</strong>
</p>

<p align="center">
  Turn prompts into hundreds of AI images and videos in just a few clicks.<br>
  Automate Google Labs workflows — manage accounts, generate character-consistent images, render videos — all locally on your machine.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/version-1.1.0-blue?style=flat-square" alt="v1.1.0">
  <img src="https://img.shields.io/badge/platform-Windows_10%2F11-0078D6?style=flat-square&logo=windows" alt="Windows">
  <img src="https://img.shields.io/badge/python-3.12-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python 3.12">
  <img src="https://img.shields.io/badge/UI-PySide6%20(Qt)-41CD52?style=flat-square&logo=qt&logoColor=white" alt="PySide6">
  <img src="https://img.shields.io/badge/license-proprietary-lightgrey?style=flat-square" alt="License">
</p>

---

## 📖 Table of Contents

- [Download & Get Started](#-download--get-started)
- [Key Features](#-key-features)
- [Screenshots](#-screenshots)
- [Architecture](#️-architecture)
- [Performance](#-performance)
- [Security](#-security)
- [Design](#-design)
- [Changelog](#-changelog)
- [Support](#-support)

---

## 🚀 Download & Get Started

1. Go to the [**Releases**](../../releases) page
2. Download the latest `.zip` archive
3. Extract to any folder
4. Run **`tplab.exe`** — done!

> **No Python installation required.** The release is a fully standalone executable with all dependencies bundled.

### System Requirements

| Requirement | Details |
| ----------- | ------- |
| **OS** | Windows 10/11 (64-bit) |
| **RAM** | 4 GB minimum, 8 GB recommended |
| **Disk** | ~500 MB for the app + browser |
| **Network** | Internet connection required |

---

## ✨ Key Features

### 🖼️ AI Image Generation

- **Whisk Service** — async image generation with automatic retry and validation
- **Flow Service** — image generation with reCAPTCHA token flow and reference image upload
- **Batch Processing** — run hundreds of prompts concurrently with smart semaphore-based throttling

### 🎭 Character-Consistent Image Generation

- `@name` syntax in prompts to reference characters
- Upload character images once — reused across all prompts in a task
- Autocomplete when typing `@` — fast and accurate

### 🎬 AI Video Generation

- **3 Generation Modes:**
  - `Text → Video` — generate video from text descriptions
  - `Reference → Video` — use reference images to guide video style
  - `Frame → Video` — frame-by-frame video generation
- **Character-Consistent Video** — combine `@name` with video generation for unified characters
- **Batch Video from Image Folder** — scan folder, map images to prompts, generate videos in bulk
- **Full Lifecycle** — submit → poll → download → save, fully automated
- **Video Concatenation** — built-in FFmpeg for merging and post-processing

### 👤 Account & Session Management

- Playwright-based browser automation with stealth mode
- Multi-account support with persistent sessions
- Automatic session recovery, cookie management, and browser header sync
- Google Labs account tier/credit status checking

### 💳 Membership & Subscription

- Google Token / License Key authentication
- Membership tier display and purchase — QR payment via SePay
- Real-time order status polling
- Subscription sync from server on startup
- **Tier-based feature gating** — features and concurrency limits enforced per subscription tier

---

## 📸 Screenshots

> _Screenshots coming soon_

<!--
Uncomment when screenshots are available:
| Feature | Preview |
| ------- | ------- |
| Image Creator | ![Image Creator](screenshots/image-creator.png) |
| Character Images | ![Character Images](screenshots/character-image-creator.png) |
| Video Creator | ![Video Creator](screenshots/video-creator.png) |
| Account Manager | ![Account Manager](screenshots/account-manager.png) |
-->

---

## 🏗️ Architecture

```text
tplab/
├── tplab.exe              # Main executable
├── playwright/            # Bundled Chromium browser + driver
│   └── driver/
│       └── package/
│           └── .local-browsers/
├── ffmpeg/                # Bundled FFmpeg for video processing
├── src/
│   └── ui/
│       └── styles/        # Theme files (Dark/Light)
└── [runtime dependencies]
```

### Tech Stack

| Component | Technology |
| --------- | ---------- |
| **UI Framework** | PySide6 (Qt for Python) |
| **Browser Engine** | Playwright + Chromium (stealth) |
| **HTTP Client** | httpx (async) |
| **Database** | SQLite (local task persistence) |
| **Data Models** | Pydantic v2 |
| **Video Processing** | FFmpeg (concat + post-processing) |
| **AI Models** | Google Whisk, Flow, Veo (video) |
| **Compiler** | Nuitka (Python → native executable) |

---

## ⚡ Performance

- **Bounded Concurrency** — semaphore throttling prevents API rate limiting
- **Non-blocking UI** — all long-running operations run on async worker threads
- **Smart Retries** — exponential backoff with clear bounds
- **Upload Once** — character images uploaded once per task, reused across all prompts
- **Model Cache** — video model config cached for 24h to reduce API calls
- **Session Persistence** — SQLite-backed task state survives app restarts

---

## 🔐 Security

- Auth tokens stored securely via Windows DPAPI (`CustomerTokenStore`)
- No sensitive data logged (token redaction)
- Isolated customer auth domain (separate from browser sessions)
- Serialized refresh token rotation — no race conditions
- Device binding via SHA256 fingerprint

---

## 🎨 Design

Supports **Dark/Light themes** — Tailwind Slate + Blue palette:

- 🌑 Dark backgrounds (`#0f172a` / `#1e293b`) for reduced eye strain
- 🔵 Blue accent colors (`#3b82f6`) for interactive elements
- ✅ WCAG AA+ compliant text contrast
- 🎯 Smooth 200ms transitions and hover effects

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
