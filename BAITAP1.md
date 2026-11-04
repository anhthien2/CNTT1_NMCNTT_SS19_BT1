### I. BÁO CÁO PHÂN TÍCH IPO

**1. Input - Dấu hiệu nhiễm Infostealer:**

-   Bị văng khỏi Facebook, Gmail,  liên tục dù vừa đổi pass.
-   Có thông báo đăng nhập lạ, đổi email khôi phục.
-   Trình duyệt tự cài tiện ích lạ, máy chạy chậm, antivirus bị tắt.
-   Tài khoản GitHub, AWS, OpenAI bị tạo token lạ, bị trừ tiền.
-   Như ảnh:  Cookie và Password trong Chrome/Edge bị đánh cắp.

**2. Process - Quy trình cấp cứu 4 bước:**

**BƯỚC 1: NGẮT KẾT NỐI NGAY LẬP TỨC - ISOLATE**  
Rút dây mạng, tắt Wi-Fi trên máy nhiễm. Không tắt máy vội để giữ log. Mục đích là chặn malware tiếp tục gửi dữ liệu và nhận lệnh từ C2 server.

**BƯỚC 2: THU HỒI QUYỀN TRUY CẬP TỪ THIẾT BỊ SẠCH - REVOKE**  

-   Đổi toàn bộ mật khẩu quan trọng theo thứ tự: Email gốc (Gmail) -> Facebook -> Ngân hàng -> GitHub -> Các dịch vụ khác.
-   Đăng xuất khỏi tất cả các phiên (Sign out all sessions).
-   Thu hồi toàn bộ Token, OAuth App, 2FA session.

**BƯỚC 3: DỌN DẸP HỆ THỐNG NHIỄM - CLEAN**  
- Không nên chỉ quét virus. Với Infostealer, chuẩn mực là cài lại trắng Windows. Vì nó có thể để lại backdoor, keylogger.

-   Format ổ C, cài lại Windows từ USB chính chủ.
-   Sau khi cài lại, cài antivirus, đổi lại toàn bộ mật khẩu lần 2.

**BƯỚC 4: KHÔI PHỤC VÀ GIÁM SÁT - MONITOR**

-   Bật lại 2FA bằng Hardware Key / App Authenticator trên thiết bị sạch.
-   Kiểm tra HaveIBeenPwned, kiểm tra lịch sử giao dịch, kiểm tra GitHub audit log trong 30 ngày tới.

**3. Output - Hệ thống sạch:**

-   Toàn bộ session/token cũ bị vô hiệu hóa.
-   Tài khoản được bảo vệ bằng mật khẩu mới + 2FA mới trên thiết bị sạch.
-   Máy tính nhiễm đã được cài lại trắng, không còn backdoor.

# II. TRIỂN KHAI CHI TIẾT 2 KỸ THUẬT

**1. "Đổi mật khẩu từ thiết bị khác" - Làm thế nào cho đúng?**

Tuyệt đối không đổi mật khẩu trên máy đang nhiễm vì bạn gõ đến đâu nó keylog đến đó.

-   Dùng điện thoại của bạn hoặc mượn máy người thân.
-   Vào /myaccount.google.com -> Bảo mật -> Đổi mật khẩu Gmail trước tiên. Gmail là chìa khóa tổng.
-   Ngay sau khi đổi, bấm **"Đăng xuất khỏi tất cả các thiết bị khác"** và **"Thu hồi quyền truy cập của ứng dụng bên thứ ba"**.
-   Làm tương tự với Facebook: Cài đặt -> Mật khẩu và bảo mật -> Nơi bạn đã đăng nhập -> Đăng xuất tất cả.
-   Bật lại 2FA ngay trên thiết bị sạch đó.

**Cách thu hồi token trên github**
- Đăng nhập vào tài khoản GitHub từ một thiết bị an toàn.

- Vào mục Settings (Cài đặt) ở góc trên bên phải, kéo xuống chọn Developer settings.

- Chọn mục Personal access tokens (hoặc Authorized OAuth Apps), kiểm tra các token/ứng dụng lạ và bấm nút Revoke để hủy quyền truy cập.
