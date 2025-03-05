**Single Instruction, Multiple Threads (SIMT)** là mô hình [[lập trình song song]] kết hợp giữa [[SIMD]]  và [[đa luồng]]. Nó được sử dụng chủ yếu trong [[GPU]] để chạy nhiều [[luồng]] thực thi cùng một lệnh nhưng trên các [[dữ liệu]] khác nhau.
### Cách hoạt động của SIMT

- Một lệnh chung → Nhiều [[luồng]] thực thi trên [[dữ liệu]] riêng biệt.  
- Mỗi [[luồng]] có thể có trạng thái riêng nhưng chia sẻ tài nguyên chung.  
- Các [[luồng]] được tổ chức thành nhóm nhỏ ([[warp|warps]] trên [[GPU]] NVIDIA) để tối ưu hiệu suất.