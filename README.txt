TRƯỜNG SƠN AI STUDIO V4.2 — ẢNH THAM CHIẾU & NHẠC RIÊNG
===================================================

Đây là bản thử nghiệm nâng cấp dựa trên V4.1. Đây CHƯA PHẢI APK và chưa được kiểm thử đầu-cuối với API trên tài khoản thật.

Thay đổi:
- Thay ô nhập khóa API cố định bằng giao diện App Key pk_ + Device Flow.
- Xin mã tại POST https://enter.pollinations.ai/api/device/code.
- Kiểm tra cấp quyền tại POST https://enter.pollinations.ai/api/device/token, mặc định mỗi 5 giây.
- Giữ access token trong sessionStorage của tab, không lưu token vào localStorage.
- Các yêu cầu ảnh/video gửi Authorization: Bearer, không đưa khóa vào URL query.
- Thêm ô chọn ảnh chân dung và xem trước; ảnh được truyền làm referenceImage khi gọi API video. Việc API chấp nhận dữ liệu ảnh dạng data URL cần được xác minh thực tế.
- Thêm ô chọn nhạc riêng từ điện thoại; khi trình duyệt hỗ trợ, nhạc được trộn vào luồng ghi WebM trên thiết bị. Đây là nhạc nền, không tự động ghép lời thoại TTS vào bản cuối.

Cách thử:
1. Giải nén ZIP.
2. Phục vụ index.html qua HTTPS hoặc localhost; file:// có thể gặp giới hạn CORS.
3. Vào Cài đặt -> nhập App Key pk_ -> Đăng nhập Pollinations.
4. Nhấn mở trang nhập mã chính thức, nhập user_code và chấp thuận.
5. Quay lại ứng dụng; thử tạo kịch bản trước.
6. Chọn ảnh chân dung hoặc file nhạc riêng nếu muốn.
7. Chỉ thử tạo ảnh/video khi tài khoản có đủ số dư; lỗi 402 nghĩa là API yêu cầu số dư mà tài khoản hiện không có.

Quan trọng:
- Đây là prototype, chưa được kiểm thử đầu-cuối trên tài khoản thật. Nếu có lỗi CORS/401/400, ghi lại thông báo lỗi, không tắt bảo mật trình duyệt.
- Device Flow được Pollinations mô tả cho CLI/headless clients; tài liệu nói flow vẫn được hỗ trợ. Trước khi phát hành, xác minh App Key được đăng ký phù hợp và kiểm tra luồng trên Android.
- sessionStorage không phải Android secure storage; script cùng trang có thể đọc token. Bản APK thật nên dùng OAuth/PKCE hoặc tích hợp native an toàn, lưu token trong Android Keystore/secure storage, kiểm tra state/expiry/revocation.
- Không nhúng khóa sk_ cá nhân cố định vào APK hoặc repository.
- API model IDs, tham số video, ảnh tham chiếu và TTS vẫn cần kiểm thử với catalog/API hiện tại.
- Ảnh chân dung sẽ được gửi đến dịch vụ AI bên ngoài khi bắt đầu tạo video. Chỉ chọn ảnh bạn đồng ý chia sẻ với dịch vụ đó.
- Chức năng nhạc phụ thuộc hỗ trợ MediaRecorder/Web Audio của trình duyệt; đầu ra thường là WebM, không đảm bảo MP4. Nhạc riêng không được tải lên máy chủ.
- Ghép video dùng MediaRecorder và thường tạo WebM, không đảm bảo MP4.
- Không có khóa API nào được thêm vào ZIP.

Tài liệu chính thức: https://gen.pollinations.ai/docs
