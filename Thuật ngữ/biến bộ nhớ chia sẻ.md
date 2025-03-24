- **[[Biến]] [[bộ nhớ]] chia sẻ** là [[biến]] được lưu trữ trong **[[bộ nhớ]] chia sẻ (Shared Memory)** của **[[khối]] (Block)** trong [[CUDA]]. Tất cả **các [[luồng]] (Threads) trong cùng một [[khối]]** có thể **truy cập và [[chia sẻ dữ liệu]]** trong [[biến]] này, giúp tối ưu [[hiệu suất]] so với [[bộ nhớ toàn cục]].
##### **Đặc điểm của [[Biến]] [[Bộ Nhớ]] Chia Sẻ**
1. **Phạm vi (Scope):**
    - Chỉ tồn tại trong **phạm vi của một [[khối]] (Block)**.
    - Chỉ các [[luồng]] trong cùng một [[khối]] mới có thể truy cập.
2. **Thời gian tồn tại (Lifetime):**
    - [[Biến]] tồn tại trong suốt **thời gian thực thi của [[khối]]**.
    - Khi [[khối]] hoàn thành, [[biến]] sẽ bị **xóa khỏi [[bộ nhớ]] chia sẻ**.
3. **Đặc tính quan trọng:**
    - Các [[luồng]] trong cùng một [[khối]] có thể **đọc/[[ghi dữ liệu]]** vào [[biến]] này.
    - **Không đảm bảo giá trị cập nhật ngay lập tức** giữa các [[luồng]].
    - Cần **đồng bộ hóa bằng `__syncthreads()`** để đảm bảo các [[luồng]] nhìn thấy giá trị mới nhất.