- **[[Biến]] [[bộ nhớ]] toàn cục** là [[biến]] được lưu trữ trong **[[bộ nhớ toàn cục]] (Global Memory)** trên [[GPU]]. Tất cả **các [[luồng]] (Threads) từ mọi [[khối]] (Blocks)** đều có thể **truy cập** vào [[biến]] này, giúp [[chia sẻ dữ liệu]] giữa các [[luồng]] một cách rộng rãi.
##### **Đặc điểm của [[Biến]] [[Bộ Nhớ]] Toàn Cục**
1. **Phạm vi (Scope):**
    - [[Biến]] được **chia sẻ trên toàn bộ [[lưới]] (Grid)**.
    - Mọi **[[luồng]] từ tất cả các [[khối]]** có thể **truy cập** cùng một [[biến]] [[bộ nhớ]] toàn cục.
2. **Thời gian tồn tại (Lifetime):**
    - **Tồn tại trong suốt vòng đời của [[ứng dụng]] [[CUDA]].**
    - **Không bị xóa khi [[khối]] hoặc [[luồng]] kết thúc**, chỉ bị giải phóng khi [[ứng dụng]] kết thúc hoặc [[lập trình viên]] giải phóng thủ công.
3. **[[Hiệu suất]] và [[độ trễ]]:**
    - **[[Độ trễ]] cao hơn [[bộ nhớ chia sẻ]] (Shared Memory) và [[Thanh ghi]] (Register).**
    - **[[Truy cập dữ liệu]] từ [[bộ nhớ toàn cục]] chậm hơn**, do đó cần có **các chiến lược đồng bộ** để đảm bảo tính nhất quán [[dữ liệu]].