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
4. **Semaphore (Tín hiệu):**
    
    - Là cơ chế đồng bộ hóa để quản lý truy cập vào tài nguyên dùng chung.
    - Đảm bảo chỉ một tiến trình được truy cập tài nguyên tại một thời điểm.
    
5. **Socket (Ổ cắm):**
    - Cho phép giao tiếp giữa các tiến trình trên cùng một máy hoặc qua mạng.
    - Sử dụng giao thức TCP/IP hoặc UDP.
6. **Signal (Tín hiệu):**
	- Dùng để thông báo sự kiện giữa các tiến trình.
7. **Remote Procedure Call (RPC - Gọi thủ tục từ xa):**
    - Cho phép một tiến trình gọi hàm hoặc thủ tục trên tiến trình khác, thậm chí trên máy tính khác.