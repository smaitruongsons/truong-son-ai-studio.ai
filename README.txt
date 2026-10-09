TRƯỜNG SƠN AI STUDIO V4.1 — DEVICE FLOW PROTOTYPE
===================================================

Đây là bản cập nhật thử nghiệm từ ZIP V4 mà bạn gửi. Đây CHƯA PHẢI APK.

Thay đổi:
- Thay ô nhập khóa API cố định bằng giao diện App Key pk_ + Device Flow.
- Xin mã tại POST https://enter.pollinations.ai/api/device/code.
- Kiểm tra cấp quyền tại POST https://enter.pollinations.ai/api/device/token, mặc định mỗi 5 giây.
- Giữ access token trong sessionStorage của tab, không lưu token vào localStorage.
- Các yêu cầu ảnh/video gửi Authorization: Bearer, không đưa khóa vào URL query.

Cách thử:
1. Giải nén ZIP.
2. Phục vụ index.html qua HTTPS hoặc localhost; file:// có thể gặp giới hạn CORS.
3. Vào Cài đặt -> nhập App Key pk_ -> Đăng nhập Pollinations.
4. Nhấn mở trang nhập mã chính thức, nhập user_code và chấp thuận.
5. Quay lại ứng dụng; khi báo đã đăng nhập, thử tạo kịch bản trước, rồi ảnh/video/audio.

Quan trọng:
- Đây là prototype, chưa được kiểm thử đầu-cuối trên tài khoản thật. Nếu có lỗi CORS/401/400, ghi lại thông báo lỗi, không tắt bảo mật trình duyệt.
- Device Flow được Pollinations mô tả cho CLI/headless clients; tài liệu nói flow vẫn được hỗ trợ. Trước khi phát hành, xác minh App Key được đăng ký phù hợp và kiểm tra luồng trên Android.
- sessionStorage không phải Android secure storage; script cùng trang có thể đọc token. Bản APK thật nên dùng OAuth/PKCE hoặc tích hợp native an toàn, lưu token trong Android Keystore/secure storage, kiểm tra state/expiry/revocation.
- Không nhúng khóa sk_ cá nhân cố định vào APK hoặc repository.
- API model IDs, tham số video và TTS trong V4 vẫn cần kiểm thử với catalog/API hiện tại.
- Ghép video dùng MediaRecorder và thường tạo WebM, không đảm bảo MP4.
- Không có khóa API nào được thêm vào ZIP.

Tài liệu chính thức: https://gen.pollinations.ai/docs
