# Bypass403 - Burp Suite Extension

**Bypass403** là một extension cho Burp Suite giúp tự động hóa quá trình kiểm thử để tìm cách vượt qua các trang/API trả về mã lỗi HTTP `403 Forbidden`. Extension được xây dựng bằng Python (Jython) với giao diện trực quan tích hợp ngay trong Burp Suite.

## Kỹ thuật hỗ trợ

*   **Path Manipulation**: Thử nghiệm chèn các ký tự đặc biệt vào đường dẫn hoặc truy vấn (ví dụ: `..;`, `%2e`, `%2f`, `;%09`, v.v.).
*   **Header Manipulation**: Chèn hoặc thay thế các HTTP Headers giả lập IP hoặc cấu hình định tuyến (ví dụ: `X-Forwarded-For`, `X-Real-IP`, `X-Forwarded-Proto`, v.v.).
*   **HTTP Method Manipulation**: Thay đổi phương thức yêu cầu từ `GET` sang `POST` đi kèm `Content-Length: 0`.
*   **Downgrade Protocol**: Hạ cấp giao thức kết nối xuống `HTTP/1.0` đồng thời xóa bỏ toàn bộ headers bổ sung.
*   **Case Sensitive**: Thay đổi kiểu viết hoa/thường của đường dẫn (ví dụ: viết hoa chữ cái đầu `/Example/Demo` hoặc xen kẽ `/ExAmPlE/DeMo`).
*   **Referer & Origin Spoofing**: Tự động sửa hoặc thêm các header `Referer` và `Origin` trỏ ngược lại chính URL của request hiện tại để đánh lừa bộ lọc của server.

## Hướng dẫn cài đặt

1.  Đảm bảo bạn đã cấu hình môi trường **Jython** trong Burp Suite (Tab **Extensions** -> **Core extension settings** -> **Python environment**).
2.  Vào tab **Extensions** -> **Installed** -> click **Add**.
3.  Chọn **Extension type** là `Python` và tìm tới đường dẫn file `Bypass403.py`.
4.  Nhấp **Next** để nạp extension.

## Hướng dẫn sử dụng

1.  Tại tab **HTTP History** (hoặc bất kỳ tab nào có request), click chuột phải vào request bị chặn `403 Forbidden` -> Chọn **Bypass 403**.
2.  Di chuyển sang tab **Bypass403** trên menu chính của Burp Suite để theo dõi tiến trình kiểm thử và phân tích kết quả.
