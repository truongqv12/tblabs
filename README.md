<p align="center">
  <h1 align="center">🧪 TP-LABS Desktop App</h1>
  <p align="center">
    <strong>Ứng dụng tạo ảnh & video AI trên Windows</strong>
  </p>
  <p align="center">
    Tự động hóa quy trình Google Labs — tạo ảnh, tạo video, quản lý tài khoản — tất cả trong một ứng dụng desktop.
  </p>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/nền_tảng-Windows-blue?style=flat-square&logo=windows" alt="Windows">
  <img src="https://img.shields.io/badge/python-3.12-green?style=flat-square&logo=python&logoColor=white" alt="Python 3.12">
  <img src="https://img.shields.io/badge/UI-PySide6%20(Qt)-41CD52?style=flat-square&logo=qt&logoColor=white" alt="PySide6">
  <img src="https://img.shields.io/badge/giấy_phép-proprietary-lightgrey?style=flat-square" alt="License">
</p>

---

## ✨ Tính năng

### 🖼️ Tạo ảnh AI
- **Whisk Service** — tạo ảnh bất đồng bộ với cơ chế retry và validation tự động
- **Flow Service** — tạo ảnh với reCAPTCHA token flow và hỗ trợ upload ảnh tham chiếu
- **Character Image Creator** — tạo ảnh nhân vật nhất quán với cú pháp `@tên` để tham chiếu
- **Xử lý hàng loạt** — giới hạn đồng thời (bounded concurrency) cho nhiều prompt cùng lúc

### 🎬 Tạo video AI
- **4 chế độ tạo video:**
  - `Văn bản → Video` — tạo video từ mô tả văn bản
  - `Ảnh tham chiếu → Video` — dùng ảnh tham chiếu để định hướng video
  - `Ảnh khởi đầu → Video` — tạo chuyển động từ một ảnh ban đầu
  - `Khung hình → Video` — tạo video theo từng khung hình
- **Reference Video Creator** — ánh xạ hàng loạt từ thư mục ảnh sang prompt
- **Quy trình tự động hoàn toàn** — gửi yêu cầu → theo dõi tiến trình → tải về → lưu file
- **Tích hợp FFmpeg** — ghép nối video và xử lý hậu kỳ

### 👤 Quản lý tài khoản & phiên làm việc
- Tự động hóa trình duyệt qua Playwright với chế độ stealth
- Hỗ trợ nhiều tài khoản với phiên làm việc lưu trữ lâu dài
- Tự động khôi phục phiên và quản lý cookie

### 💳 Thành viên & Gói đăng ký
- Đăng nhập bằng Google Token hoặc License Key
- Hiển thị và mua các gói thành viên
- Theo dõi trạng thái đơn hàng theo thời gian thực
- Đồng bộ gói đăng ký từ server khi khởi động app

---

## 🚀 Hướng dẫn sử dụng

### Tải bản build sẵn

1. Truy cập trang [**Releases**](../../releases)
2. Tải file `.zip` phiên bản mới nhất
3. Giải nén vào thư mục bất kỳ
4. Chạy file `tplab.exe`

> **Không cần cài Python** — bản release đã đóng gói toàn bộ dependencies, chạy trực tiếp.

### Yêu cầu hệ thống

| Yêu cầu | Chi tiết |
|----------|----------|
| **Hệ điều hành** | Windows 10/11 (64-bit) |
| **RAM** | Tối thiểu 4 GB, khuyến nghị 8 GB |
| **Ổ cứng** | ~500 MB cho app + trình duyệt |
| **Mạng** | Cần kết nối Internet |

---

## 📸 Ảnh chụp màn hình

> _Sẽ cập nhật sớm_

<!-- 
Bỏ comment khi có ảnh:
| Tính năng | Xem trước |
|-----------|-----------|
| Tạo ảnh | ![Tạo ảnh](screenshots/image-creator.png) |
| Tạo video | ![Tạo video](screenshots/video-creator.png) |
| Quản lý tài khoản | ![Quản lý tài khoản](screenshots/account-manager.png) |
-->

---

## 🏗️ Cấu trúc bản build

```
tplab/
├── tplab.exe              # File chạy chính
├── playwright/            # Trình duyệt Chromium đi kèm
│   └── driver/
│       └── package/
│           └── .local-browsers/
├── ffmpeg/                # FFmpeg đi kèm cho xử lý video
├── src/
│   └── ui/
│       └── styles/        # File giao diện QSS (Dark theme)
└── [thư viện runtime]
```

### Công nghệ sử dụng

| Thành phần | Công nghệ |
|------------|-----------|
| **Giao diện** | PySide6 (Qt for Python) |
| **Trình duyệt** | Playwright + Chromium |
| **HTTP Client** | httpx (bất đồng bộ) |
| **Cơ sở dữ liệu** | SQLite (lưu trữ task cục bộ) |
| **Data Models** | Pydantic v2 |
| **Xử lý video** | FFmpeg |
| **Đóng gói** | Nuitka (Python → file .exe gốc) |

---

## 🎨 Thiết kế giao diện

Ứng dụng sử dụng **giao diện tối hiện đại** theo bảng màu Tailwind Slate + Blue:

- 🌑 Nền tối (`#0f172a` / `#1e293b`) — giảm mỏi mắt khi sử dụng lâu
- 🔵 Màu nhấn xanh dương (`#3b82f6`) — cho các phần tử tương tác
- ✅ Đạt chuẩn WCAG AA+ về độ tương phản chữ
- 🎯 Hiệu ứng chuyển tiếp mượt mà

---

## ⚡ Hiệu năng

- **Giới hạn đồng thời** — throttle bằng semaphore, tránh bị rate limit API
- **Giao diện không bị đơ** — mọi tác vụ nặng chạy trên worker thread riêng
- **Retry thông minh** — chính sách retry có giới hạn với exponential backoff
- **Lưu trữ trạng thái** — task state lưu trên SQLite, app restart không mất dữ liệu

---

## 🔐 Bảo mật

- Token xác thực được lưu trữ an toàn qua `CustomerTokenStore`
- Không ghi log dữ liệu nhạy cảm
- Tách biệt hoàn toàn domain xác thực khách hàng với phiên trình duyệt
- Cơ chế làm mới token với chính sách retry đơn lần

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
