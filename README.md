<p align="center">
  <img src="assets/logo.png" alt="TP-LABS Logo" width="120">
</p>

<h1 align="center">🧪 TP-LABS Desktop App</h1>

<p align="center">
  <strong>Tạo ảnh & video AI hàng loạt — tự động hoàn toàn trên Windows</strong>
</p>

<p align="center">
  Biến prompt thành hàng trăm ảnh và video AI chỉ trong vài click.<br>
  Tự động hóa Google Labs — quản lý tài khoản, tạo ảnh nhân vật nhất quán, render video — tất cả offline trên máy bạn.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/phiên_bản-1.1.0-blue?style=flat-square" alt="v1.1.0">
  <img src="https://img.shields.io/badge/nền_tảng-Windows_10%2F11-0078D6?style=flat-square&logo=windows" alt="Windows">
  <img src="https://img.shields.io/badge/python-3.12-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python 3.12">
  <img src="https://img.shields.io/badge/UI-PySide6%20(Qt)-41CD52?style=flat-square&logo=qt&logoColor=white" alt="PySide6">
  <img src="https://img.shields.io/badge/giấy_phép-proprietary-lightgrey?style=flat-square" alt="License">
</p>

---

## 📖 Mục lục

- [Tải về & Bắt đầu ngay](#-tải-về--bắt-đầu-ngay)
- [Tính năng chính](#-tính-năng-chính)
- [Ảnh chụp màn hình](#-ảnh-chụp-màn-hình)
- [Kiến trúc](#️-kiến-trúc)
- [Hiệu năng](#-hiệu-năng)
- [Bảo mật](#-bảo-mật)
- [Giao diện](#-giao-diện)
- [Lịch sử thay đổi](#-lịch-sử-thay-đổi)
- [Hỗ trợ](#-hỗ-trợ)

---

## 🚀 Tải về & Bắt đầu ngay

1. Truy cập trang [**Releases**](../../releases)
2. Tải file `.zip` phiên bản mới nhất
3. Giải nén vào thư mục bất kỳ
4. Chạy **`tplab.exe`** — xong!

> **Không cần cài Python.** Bản release đã đóng gói sẵn toàn bộ — chạy trực tiếp.

### Yêu cầu hệ thống

| Yêu cầu | Chi tiết |
|----------|----------|
| **Hệ điều hành** | Windows 10/11 (64-bit) |
| **RAM** | Tối thiểu 4 GB, khuyến nghị 8 GB |
| **Ổ cứng** | ~500 MB cho app + trình duyệt |
| **Mạng** | Cần kết nối Internet |

---

## ✨ Tính năng chính

### 🖼️ Tạo ảnh AI

- **Whisk Service** — tạo ảnh bất đồng bộ với retry và validation tự động
- **Flow Service** — tạo ảnh với reCAPTCHA token flow và upload ảnh tham chiếu
- **Xử lý hàng loạt** — chạy hàng trăm prompt cùng lúc với giới hạn đồng thời thông minh

### 🎭 Tạo ảnh nhân vật nhất quán

- Cú pháp `@tên` trong prompt để tham chiếu nhân vật
- Upload ảnh nhân vật 1 lần — tái sử dụng cho toàn bộ prompt trong task
- Autocomplete khi gõ `@` — nhanh và chính xác

### 🎬 Tạo video AI

- **3 chế độ tạo video:**
  - `Văn bản → Video` — tạo video từ mô tả văn bản
  - `Ảnh tham chiếu → Video` — dùng ảnh để định hướng phong cách video
  - `Khung hình → Video` — tạo video theo từng khung hình
- **Video nhân vật nhất quán** — kết hợp `@tên` với video, giữ nhân vật đồng nhất
- **Video từ thư mục ảnh** — quét thư mục, ánh xạ ảnh sang prompt, tạo video hàng loạt
- **Quy trình tự động** — gửi yêu cầu → theo dõi → tải về → lưu file
- **Ghép video** — tích hợp FFmpeg để nối và xử lý hậu kỳ

### 👤 Quản lý tài khoản & phiên

- Tự động hóa trình duyệt qua Playwright (chế độ stealth)
- Hỗ trợ nhiều tài khoản với phiên làm việc lưu trữ lâu dài
- Tự động khôi phục phiên, quản lý cookie, đồng bộ header trình duyệt
- Kiểm tra tier/credit tài khoản Google Labs

### 💳 Thành viên & Gói đăng ký

- Đăng nhập bằng Google Token hoặc License Key
- Xem và mua gói thành viên — thanh toán QR qua SePay
- Theo dõi trạng thái đơn hàng theo thời gian thực
- Đồng bộ gói đăng ký từ server khi khởi động
- **Phân quyền theo gói** — giới hạn tính năng và số luồng đồng thời theo tier

---

## 📸 Ảnh chụp màn hình

> _Sẽ cập nhật sớm_

<!--
Bỏ comment khi có ảnh:
| Tính năng | Xem trước |
|-----------|-----------|
| Tạo ảnh | ![Tạo ảnh](screenshots/image-creator.png) |
| Ảnh nhân vật | ![Ảnh nhân vật](screenshots/character-image-creator.png) |
| Tạo video | ![Tạo video](screenshots/video-creator.png) |
| Quản lý tài khoản | ![Quản lý tài khoản](screenshots/account-manager.png) |
-->

---

## 🏗️ Kiến trúc

```
tplab/
├── tplab.exe              # File chạy chính
├── playwright/            # Trình duyệt Chromium đi kèm
│   └── driver/
│       └── package/
│           └── .local-browsers/
├── ffmpeg/                # FFmpeg cho xử lý video
├── src/
│   └── ui/
│       └── styles/        # Giao diện (Dark/Light theme)
└── [thư viện runtime]
```

### Công nghệ

| Thành phần | Công nghệ |
|------------|-----------|
| **Giao diện** | PySide6 (Qt for Python) |
| **Trình duyệt** | Playwright + Chromium (stealth) |
| **HTTP Client** | httpx (bất đồng bộ) |
| **Cơ sở dữ liệu** | SQLite (lưu trữ task cục bộ) |
| **Data Models** | Pydantic v2 |
| **Xử lý video** | FFmpeg (ghép nối + hậu kỳ) |
| **AI Models** | Google Whisk, Flow, Veo (video) |
| **Đóng gói** | Nuitka (Python → native .exe) |

---

## ⚡ Hiệu năng

- **Giới hạn đồng thời** — semaphore throttle, tránh rate limit API
- **Giao diện mượt mà** — mọi tác vụ nặng chạy trên worker thread riêng
- **Retry thông minh** — exponential backoff với giới hạn rõ ràng
- **Upload 1 lần** — ảnh nhân vật upload 1 lần, tái sử dụng cho toàn bộ prompt
- **Cache model** — cấu hình video model cache 24h, giảm API call
- **Lưu trữ trạng thái** — task state trên SQLite, restart app không mất dữ liệu

---

## 🔐 Bảo mật

- Token lưu trữ an toàn qua Windows DPAPI (`CustomerTokenStore`)
- Không ghi log dữ liệu nhạy cảm (token redaction)
- Tách biệt hoàn toàn domain xác thực khách hàng với phiên trình duyệt
- Refresh token serialized — tránh race condition khi rotate
- Device binding qua SHA256 fingerprint

---

## 🎨 Giao diện

Hỗ trợ **Dark/Light theme** — bảng màu Tailwind Slate + Blue:

- 🌑 Nền tối (`#0f172a` / `#1e293b`) — giảm mỏi mắt
- 🔵 Màu nhấn xanh dương (`#3b82f6`) — phần tử tương tác
- ✅ Đạt chuẩn WCAG AA+ về độ tương phản
- 🎯 Hiệu ứng chuyển tiếp mượt mà 200ms

---

## 📋 Lịch sử thay đổi

Xem [CHANGELOG](docs/project-changelog.md) để theo dõi lịch sử phiên bản.

---

## 🤝 Hỗ trợ

Nếu gặp vấn đề hoặc có câu hỏi:

- 📧 Liên hệ đội phát triển
- 🐛 Tạo issue trong repository này

---

## 📄 Giấy phép

Phần mềm độc quyền. Bảo lưu mọi quyền.

---

<p align="center">
  <sub>Được xây dựng với ❤️ bằng Python, PySide6 và Playwright</sub>
</p>
