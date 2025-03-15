**Phương thức giao tiếp giữa các tiến trình (Inter-Process Communication - IPC)** là các cơ chế và kỹ thuật cho phép các tiến trình (process) trong hệ thống máy tính trao đổi dữ liệu và phối hợp hoạt động với nhau. Các tiến trình có thể chạy trên cùng một máy tính hoặc trên các máy tính khác nhau trong mạng.

### Các phương thức giao tiếp giữa các tiến trình phổ biến:

1. **Pipe (Ống dẫn):**
    - Là một cơ chế giao tiếp một chiều giữa hai tiến trình.
2. **Message Queue (Hàng đợi tin nhắn):**
    - Cho phép các tiến trình gửi và nhận tin nhắn thông qua một hàng đợi.
    - Tin nhắn có thể có cấu trúc và độ dài khác nhau.
3. **Shared Memory (Bộ nhớ dùng chung):**
    - Các tiến trình chia sẻ một vùng bộ nhớ chung để trao đổi dữ liệu.
    - Hiệu quả về tốc độ nhưng cần cơ chế đồng bộ hóa (ví dụ: semaphore) để tránh xung đột.