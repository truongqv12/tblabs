<p align="center">
  <img src="assets/logo/tp-labs_pixel_lettermark_03.png" alt="TP-LABS Logo" width="120">
</p>

<h1 align="center">TP-LABS Desktop App</h1>

<p align="center">
  <strong>Batch-generate hundreds of AI images & videos — fully automated on Windows</strong>
</p>

<p align="center">
  No more one-by-one clicking. TP-LABS turns your prompts into hundreds of AI images and videos in minutes.<br>
  Character-consistent generation, sequential video stitching, automated account management.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/version-1.1.5-blue?style=flat-square" alt="v1.1.5">
  <img src="https://img.shields.io/badge/platform-Windows_10%2F11-0078D6?style=flat-square&logo=windows" alt="Windows">
  <img src="https://img.shields.io/badge/python-3.12-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python 3.12">
  <img src="https://img.shields.io/badge/UI-PySide6%20(Qt)-41CD52?style=flat-square&logo=qt&logoColor=white" alt="PySide6">
  <img src="https://img.shields.io/badge/engine-Veo%203.1-10b981?style=flat-square" alt="Veo 3.1">
  <img src="https://img.shields.io/badge/license-proprietary-lightgrey?style=flat-square" alt="License">
</p>

---

## Screenshots

### Character-Consistent Image Generation

> Use `@name` syntax to keep characters unified across hundreds of images — upload once, reuse forever.

![Character-Consistent Image Generation](assets/screenshot/char_to_image.png)

### Character-Consistent Video Generation

> Combine character images with video prompts — batch-generate videos while keeping style and characters consistent.

![Character-Consistent Video Generation](assets/screenshot/video_to_Image.png)

### Sequential Frame Stitching

> Enter multiple transition prompts with reference images — the app creates a seamless video sequence.

![Sequential Frame — Input](assets/screenshot/sequential_frame.png)

> Track progress per prompt in real time, preview video and input images right in the table.

![Sequential Frame — Running](assets/screenshot/sequential_frame_run.png)

### Frame-to-Video Generation

> Select start frame + end frame, describe the motion — Veo 3.1 generates the video. Supports batch processing.

![Frame-to-Video Generation](assets/screenshot/frametoimg.png)

---

## Download & Get Started

1. Go to the [**Releases**](../../releases) page
2. Download the latest `.zip` archive
3. Extract to any folder
4. Run **`tplab.exe`** — done!

> **No Python installation required.** The release is fully standalone with all dependencies bundled.

### System Requirements

| Requirement | Details |
| ----------- | ------- |
| **OS** | Windows 10/11 (64-bit) |
| **RAM** | 4 GB minimum, 8 GB recommended |
| **Disk** | ~616 MB for the app + browser |
| **Network** | Internet connection required |

---

## Key Features

### Batch AI Image Generation

- **Whisk Service** — async image generation with automatic retry and validation
- **Flow Service** — image generation with reference image upload and advanced processing
- **Batch Processing** — run hundreds of prompts concurrently with smart throttling to avoid rate limits

### Character-Consistent Images

- `@name` syntax in prompts to reference characters
- Upload character images once — reused across all prompts in a task
- Autocomplete when typing `@` — fast and accurate

### AI Video Generation

- **3 Generation Modes:**
  - `Text → Video` — generate video from text descriptions
  - `Reference → Video` — use reference images to guide video style
  - `Frame → Video` — select start + end frames, describe the motion
- **Character-Consistent Video** — combine `@name` with video for unified characters
- **Batch Video from Image Folder** — scan folder, map images to prompts, generate videos in bulk
- **Full Lifecycle** — submit → poll → download → save, fully automated
- **Video Concatenation** — built-in FFmpeg for merging and post-processing

### Sequential Frame Stitching *(New)*

- Enter multiple transition prompts in sequence, each with reference images
- App generates seamless sequential video — preview inputs and track progress in real time
- Result: a continuous video chain with connected content from start to finish

### Account & Session Management

- Multi-account support with persistent sessions
- Automatic session recovery and cookie management
- Google Labs account tier/credit status checking

### Membership & Subscription

- Google Token / License Key authentication
- Purchase membership tiers — QR payment via SePay
- Real-time order status tracking
- **Tier-based feature gating** — features and concurrency limits enforced per subscription tier

### Advanced Task Management *(New)*

- Custom naming for each task, filter by page type (image/video/character)
- Quick search, real-time progress bars
- Delete tasks with automatic output folder cleanup (with confirmation)

---

## Architecture

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
| **Browser Engine** | Playwright + Chromium |
| **HTTP Client** | httpx (async) |
| **Database** | SQLite (local task persistence) |
| **Data Models** | Pydantic v2 |
| **Video Processing** | FFmpeg (concat + post-processing) |
| **AI Models** | Google Whisk, Flow, Veo 3.1 |
| **Compiler** | Nuitka (Python → native executable) |

---

## Performance

- **Bounded Concurrency** — semaphore throttling prevents API rate limiting
- **Non-blocking UI** — all long-running operations run on async worker threads
- **Smart Retries** — exponential backoff with clear bounds
- **Upload Once** — character images uploaded once per task, reused across all prompts
- **Model Cache** — video model config cached for 24h to reduce API calls
- **Session Persistence** — SQLite-backed task state survives app restarts

---

## Security

- Auth tokens stored securely via Windows DPAPI
- No sensitive data logged (token redaction)
- Isolated customer auth domain (separate from browser sessions)
- Serialized refresh token rotation — no race conditions
- Device-bound authentication — one session per machine

---

## Design

Supports **Dark/Light themes** — Tailwind Slate + Blue palette:

- Dark backgrounds (`#0f172a` / `#1e293b`) for reduced eye strain
- Blue accent colors (`#3b82f6`) for interactive elements
- WCAG AA+ compliant text contrast
- Smooth 200ms transitions and hover effects

---

## Changelog

See [CHANGELOG](CHANGELOG.md) for version history and release notes.

---

## Support

If you encounter any issues or have questions:

- Contact the development team
- Open an issue in this repository

---

## License

This software is proprietary. All rights reserved.

---

<p align="center">
  <sub>Built with Python, PySide6, and Playwright</sub>
</p>
