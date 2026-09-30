# Ads Autopilot

Buồng lái quảng cáo đa nền tảng — demo giao diện kết nối Facebook, Google Ads và Zalo để tự động lên chiến dịch quảng cáo từ một link Fanpage / OA / Website.

**Xem trực tiếp:** mở `index.html` trong trình duyệt, hoặc bật GitHub Pages cho repo này (Settings → Pages → Deploy from branch `main` / `root`).

## Đây là bản demo giao diện

Toàn bộ dữ liệu (chi tiêu, CTR, CPA, chuyển đổi...) là dữ liệu mẫu cố định trong `index.html`, chưa gọi API thật của nền tảng nào.

**Quan trọng về bảo mật:** app này chủ động **không** có ô nhập mật khẩu ở bất kỳ đâu. Luồng "Kết nối" mô phỏng đăng nhập OAuth (cửa sổ đăng nhập chính thức của Meta/Google/Zalo cấp quyền, không chia sẻ mật khẩu cho bên thứ ba) — đúng với cách các nền tảng này yêu cầu tích hợp hợp lệ. Tự động hoá đăng nhập bằng mật khẩu thô vi phạm Điều khoản dịch vụ của cả ba nền tảng và dễ khiến tài khoản bị khoá.

## Tính năng trong bản demo

1. **Kết nối nền tảng** — 3 thẻ Facebook / Google Ads / Zalo, mô phỏng luồng OAuth.
2. **Tạo chiến dịch tự động** — dán link Fanpage/OA/Website → app tự nhận diện nền tảng và tạo preview → cấu hình mục tiêu/ngân sách/số ngày → chạy chiến dịch (mô phỏng chi tiêu tăng dần theo thời gian thực).
3. **Dashboard hiệu suất** — chỉ số tổng quan, biểu đồ chi tiêu theo nền tảng và theo 14 ngày.
4. **Phân tích & đề xuất tối ưu** — đọc dữ liệu chi tiêu/CPA/CTR/tần suất hiển thị, tự tính tăng trưởng tuần-qua-tuần và sinh danh sách đề xuất hành động (tăng/giảm ngân sách theo kênh, cảnh báo ad fatigue, gợi ý A/B test) xếp theo mức ưu tiên.

## Bước tiếp theo để chạy thật

Thay các hàm mô phỏng (`setTimeout` connect, mảng `data`/`platformMetrics` cố định) bằng tích hợp thật:

- **Facebook/Meta**: [Meta Marketing API](https://developers.facebook.com/docs/marketing-apis/) qua OAuth (Meta for Developers — cần Meta App ID/Secret).
- **Google Ads**: [Google Ads API](https://developers.google.com/google-ads/api/docs/start) qua OAuth 2.0 (Google Cloud project + Developer Token).
- **Zalo**: [Zalo Official Account API / Zalo Ads API](https://developers.zalo.me/) qua OAuth (Zalo App ID).

Việc gọi các API trên cần thực hiện từ backend (không lộ client secret ở phía trình duyệt).
