# Bypass403 - Burp Suite Extension

**Bypass403** là một extension cho Burp Suite giúp tự động hóa quá trình kiểm thử để tìm cách vượt qua các trang/API trả về mã lỗi HTTP `403 Forbidden`. Extension được xây dựng bằng Python (Jython) với giao diện trực quan tích hợp ngay trong Burp Suite.

## Tính năng nổi bật

*   **Giao diện Trực quan (Tab Bypass403)**:
    *   Cấu hình động danh sách payloads (thêm/sửa/xóa trực tiếp trên GUI).
    *   Hiển thị tất cả kết quả test case dưới dạng bảng (`JTable`) hỗ trợ sắp xếp (sort) theo các cột.
    *   Xem chi tiết Request/Response cạnh nhau (Horizontal Layout).
    *   Có nút **Clear Table** để dọn dẹp nhanh kết quả.
*   **Highlight kết quả thành công**: Tự động bôi màu xanh lá đối với các yêu cầu bypass thành công (Status Code `200`).
*   **Các kỹ thuật kiểm thử tự động**:
    *   Chèn ký tự đặc biệt vào Query/Path (ví dụ: `..;`, `%2e`, `%2f`, `;%09`, v.v.).
    *   Chèn/Thay thế các HTTP Headers giả lập IP/Routing (ví dụ: `X-Forwarded-For`, `X-Real-IP`, v.v.).
    *   Thử nghiệm thay đổi Method từ `GET` sang `POST` với `Content-Length: 0`.
    *   Thử nghiệm hạ cấp giao thức HTTP xuống `HTTP/1.0` và xóa bỏ toàn bộ headers.

## Hướng dẫn cài đặt

1.  Đảm bảo bạn đã cài đặt môi trường **Jython** (Python cho Java) trong Burp Suite:
    *   Tải file Jython Standalone `.jar`.
    *   Cấu hình đường dẫn Jython Jar tại tab **Extensions** -> **Extension settings** -> **Python environment**.
2.  Tải extension:
    *   Vào tab **Extensions** -> **Installed** -> click **Add**.
    *   Chọn **Extension type** là `Python`.
    *   Chọn đường dẫn đến file `Bypass403.py`.
    *   Nhấp **Next** để nạp extension.

## Hướng dẫn sử dụng

1.  Tìm kiếm request bị chặn với mã trạng thái `403 Forbidden` trong tab **HTTP History** hoặc các tab khác.
2.  Click chuột phải vào Request -> Chọn **Bypass 403**.
3.  Di chuyển sang tab **Bypass403** trên menu chính của Burp Suite để theo dõi tiến trình chạy thử, xem chi tiết Request/Response.
