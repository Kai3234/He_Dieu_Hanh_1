**Cơ chế khóa** trong [[khoa học máy tính]] là một phương pháp được sử dụng để **đảm bảo tính đồng bộ** khi nhiều [[tiến trình]] hoặc [[luồng]] (threads) cùng truy cập và thao tác trên một tài nguyên dùng chung (shared resource). Mục đích chính của cơ chế khóa là **ngăn chặn các tình huống tranh chấp dữ liệu ([[Race condition|race conditions]])**, đảm bảo rằng chỉ có một tiến trình hoặc luồng được phép truy cập vào tài nguyên đó tại một thời điểm nhất định.

## **Các loại cơ chế khóa phổ biến**

- **Mutex (Mutual Exclusion Lock):**
    
    - Chỉ cho phép một tiến trình hoặc luồng truy cập tài nguyên tại một thời điểm.
    - Khi một luồng giữ mutex, các luồng khác phải chờ cho đến khi mutex được giải phóng.
- **Semaphore:**
    
    - Cho phép giới hạn số lượng tiến trình truy cập tài nguyên cùng một lúc.
    - Có thể dùng để đồng bộ hóa nhiều tiến trình mà không chỉ giới hạn ở 1 như mutex.
- **Spinlock:**
    
    - Luồng chờ đợi (spin) liên tục cho đến khi khóa được giải phóng.
    - Thường dùng trong các hệ thống đa lõi, nơi thời gian chờ đợi ngắn và chuyển ngữ nhanh chóng.
- **Read-Write Lock:**
    
    - Cho phép nhiều luồng đọc dữ liệu đồng thời nhưng chỉ cho phép một luồng ghi dữ liệu tại một thời điểm.
    - Phù hợp với các ứng dụng có nhiều thao tác đọc và ít thao tác ghi.
- **Lock-Free và Wait-Free:**
    
    - Các thuật toán và cấu trúc dữ liệu được thiết kế để tránh sử dụng khóa, giúp tăng hiệu suất trong môi trường đa luồng.