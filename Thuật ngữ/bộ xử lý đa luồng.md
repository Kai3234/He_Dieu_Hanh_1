- **[[Bộ xử lý]] [[đa luồng]] (Streaming Multiprocessor - [[SM]])** là [[đơn vị xử lý]] chính trong kiến trúc [[GPU]] của NVIDIA, chịu trách nhiệm **xử lý hàng nghìn [[luồng]] (threads) song song**.
##### **Cấu trúc của [[SM]] trong [[GPU]]**
- Mỗi [[GPU]] bao gồm nhiều **Streaming Multiprocessors (SMs)**, trong đó **mỗi [[SM]] có nhiều [[đơn vị xử lý]] nhỏ hơn gọi là [[CUDA]] Cores**.
- Một [[SM]] thường bao gồm:
    1. **[[CUDA]] Cores**: [[đơn vị xử lý]] toán học và logic ([[ALU]]).
    2. **[[Warp]] Scheduler**: Bộ lập lịch, quản lý [[luồng]] theo nhóm 32 [[luồng]] ([[warp]]).
    3. **[[Bộ nhớ chia sẻ]] (Shared Memory)**: [[Bộ nhớ]] tốc độ cao, dùng chung giữa các [[luồng]] trong một [[SM]].
    4. **[[Tệp thanh ghi]]** (Register File)**: Lưu trữ [[biến]] của từng [[luồng]] riêng biệt.
    5. **[[Bộ nhớ đệm]] (L1 Cache)**: Giảm [[độ trễ]] khi [[truy cập bộ nhớ]] toàn cục.

##### **Cách hoạt động của [[SM]]**
- Mỗi [[SM]] có thể xử lý nhiều **[[khối luồng]] (blocks)** cùng một lúc.
- Trong một [[SM]], các [[luồng]] được chia thành **nhóm 32 [[luồng]] gọi là [[Warp]]** và được lập lịch thực thi đồng thời.
- [[SM]] giúp [[GPU]] thực hiện **hàng nghìn [[luồng]] đồng thời**, tăng tốc xử lý [[tính toán song song]].