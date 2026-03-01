# Nhật ký cập nhật — TP-Labs Desktop

## v1.1.5 — 02/03/2026

**Tối ưu hệ thống**

- Cải thiện hiệu năng xử lý nền, giảm tải tài nguyên khi chạy nhiều task đồng thời.

---

## v1.1.4 — 01/03/2026

**Quản lý task hoàn toàn mới + Giao diện đẹp hơn**

- Quản lý task: đặt tên riêng, lọc theo loại (ảnh/video/character), tìm kiếm nhanh, xem tiến độ bằng thanh progress, xóa task kèm dọn file
- Header mỗi trang hiển thị tiêu đề riêng, badge gói dịch vụ rõ ràng hơn
- Sửa lỗi màu sắc badge trên giao diện sáng

---

## v1.1.3 — 01/03/2026

**Bảng prompt gọn gàng hơn**

- Bảng hiển thị prompt nhỏ gọn hơn, badge trạng thái dạng pill, prompt tự xuống dòng
- Hiệu ứng hover với thanh accent bên trái

---

## v1.1.2 — 01/03/2026

**Giao diện khung hình → video mới**

- Thiết kế dạng card cho từng khung hình: xem trước ảnh đầu/cuối, prompt có đếm ký tự
- Click vào thumbnail để xem ảnh gốc

---

## v1.1.1 — 01/03/2026

**Sidebar mới**

- Sidebar thiết kế lại: icon + text, màu nhấn riêng cho từng trang, khóa trang theo gói dịch vụ

---

## v1.1.0 — 01/03/2026

**Tính năng mới: Video đồng nhất**

- Tạo video với nhân vật cố định bằng cú pháp `@tên` — giống ảnh đồng nhất nhưng cho video
- Ảnh nhân vật upload 1 lần, lưu lại để dùng tiếp nếu app bị tắt đột ngột

---

## v0.11.29 — 01/03/2026

- Bỏ dropdown chọn task cũ, thay bằng nút "Tạo mới" rõ ràng hơn
- Nút retry có màu sắc phân biệt trạng thái

---

## v0.11.28 — 28/02/2026

- Kiểm soát đồng thời trên tất cả 5 trang tạo nội dung
- Retry task tái sử dụng project cũ — không tạo trùng
- Thêm dialog Giới thiệu
- Pipeline CI/CD tự động build

---

## v0.11.27 — 28/02/2026

**Phân quyền theo gói dịch vụ**

- Trang bị khóa hiển thị mờ + icon khóa nếu chưa đủ gói
- Giới hạn đồng thời theo tier, cảnh báo khi vượt
- Nút nâng cấp gói ngay trong app

---

## v0.11.26 — 28/02/2026

**Tính năng mới: Ảnh đồng nhất**

- Tạo ảnh với nhân vật cố định bằng cú pháp `@tên` + autocomplete
- Ảnh nhân vật chỉ upload 1 lần, tiết kiệm thời gian

---

## v0.11.25 — 28/02/2026

- Cập nhật hệ thống xử lý video: upload, request, polling, download theo format mới
- Cải thiện cấu trúc dữ liệu video

---

## v0.11.24 — 27/02/2026

- Nâng cấp model tạo ảnh mới, đồng bộ hệ thống tốt hơn
- Tăng cường bảo mật log

---

## v0.11.18 → v0.11.23 — 19/02 đến 24/02/2026

**Hệ thống gói dịch vụ**

- Đăng nhập bằng Google hoặc license key
- Mua gói qua QR SePay, xác nhận tự động
- Đồng bộ gói khi mở app và sau khi thanh toán
- Kiểm tra đơn hàng chờ tự động ở nền

---

## v0.11.5 → v0.11.17 — 07/02 đến 15/02/2026

**Nền tảng**

- Tạo video với retry thông minh, chọn model tự động từ API
- Tối ưu hệ thống xử lý nền
- Sidebar config, trang video tham chiếu, quản lý task thống nhất
