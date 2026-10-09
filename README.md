# ElectroLab – Chatbot tính toán điện (Công nghệ 12)

Trang học tập dựa theo Bài 9: Thiết bị điện trong hệ thống điện gia đình (Kết nối tri thức).

**Repository:** https://github.com/triducit-art/chatbot-tinh-toan-dien
**Địa chỉ GitHub Pages dự kiến:** https://triducit-art.github.io/chatbot-tinh-toan-dien/

## Chức năng

- Tính công suất tổng của một hoặc nhiều thiết bị điện.
- Tính dòng điện một pha: I = P / (U × cosφ).
- Tính tiết diện dây tham khảo: S = I / J.
- Tính dòng aptomat tham khảo: Iđm = I × h_at.
- Hiển thị lời giải theo từng bước và cảnh báo phối hợp dây dẫn – aptomat.
- Hỏi đáp theo quy tắc SGK; có thể kết nối thêm Gemini AI qua dịch vụ bảo mật.

File index.html ở thư mục gốc là **phiên bản độc lập một tệp**; không cần cài Node.js, cơ sở dữ liệu hoặc API để sử dụng máy tính điện và chatbot theo quy tắc.

## Bật GitHub Pages

1. Mở https://github.com/triducit-art/chatbot-tinh-toan-dien/settings/pages
2. Tại **Build and deployment**, chọn **Source: Deploy from a branch**.
3. Chọn **Branch: main**, thư mục **/(root)**, rồi nhấn **Save**.
4. Đợi GitHub xuất bản, sau đó truy cập: https://triducit-art.github.io/chatbot-tinh-toan-dien/

Nếu trang chưa mở được, vào tab Actions để xem lịch sử xuất bản và kiểm tra lại Settings → Pages. Việc đưa mã nguồn lên GitHub **không có nghĩa** GitHub Pages đã được bật.

## Bật hội thoại Gemini AI (tùy chọn)

GitHub Pages là trang web tĩnh, **không được đặt GEMINI_API_KEY vào index.html hoặc repository công khai**. Mã máy chủ trung gian nằm trong thư mục worker/, sử dụng Cloudflare Workers. Cần tài khoản Cloudflare, một Gemini API key do giáo viên quản lý và quyền triển khai Worker.

1. Tạo API key tại https://aistudio.google.com/apikey và giữ bí mật.
2. Trong thư mục worker/, chạy npx wrangler login, tiếp đó npx wrangler deploy.
3. Chạy npx wrangler secret put GEMINI_API_KEY và nhập khóa khi được yêu cầu (không commit khóa).
4. Nếu cần, chỉnh model GEMINI_MODEL trong worker/wrangler.toml. ALLOWED_ORIGINS đã đặt là https://triducit-art.github.io.
5. Sao chép URL Workers (HTTPS) vào mục **Cài đặt AI** trên website; nhấn **Kiểm tra kết nối** rồi **Lưu địa chỉ AI**.

Worker chưa được triển khai chỉ bằng việc tải mã vào GitHub. Khi chưa có Worker và API key, phần tính toán và chatbot quy tắc vẫn hoạt động.

**Lưu ý bảo mật và chi phí:** ALLOWED_ORIGINS/CORS chỉ hạn chế một số yêu cầu từ trình duyệt, **không phải cơ chế xác thực**. Để cho nhiều học sinh sử dụng, cần thêm kiểm soát truy cập, giới hạn tốc độ/lượt gọi và theo dõi chi phí Gemini; không thu thập thông tin cá nhân của học sinh.

## Lưu ý an toàn

Công thức và các mức chọn được đơn giản hóa theo bài học. Kết quả chỉ là **tham khảo để học tập**, không sử dụng làm căn cứ mua sắm hay lắp đặt điện thật. Khi thi công phải đánh giá điều kiện đi dây, dòng cho phép thực tế, sụt áp, khả năng cắt ngắn mạch, thiết bị bảo vệ chống điện giật và các quy chuẩn hiện hành bởi người có chuyên môn.

**Nguồn học liệu:** Bài 9 Công nghệ 12 – Kết nối tri thức, nội dung về công suất, dây dẫn và aptomat, trang 47–49. Không đưa PDF SGK lên repository công khai.
