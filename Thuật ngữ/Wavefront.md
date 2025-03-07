**Wavefront** là một nhóm các **[[luồng]] chạy song song** trên **[[GPU]] AMD**. Nó là đơn vị thực thi cơ bản trong kiến trúc **AMD GCN (Graphics Core Next) và RDNA (Radeon DNA)**, tương tự như **[[Warp]] trên [[GPU]] NVIDIA**.
- **Wavefront** là một nhóm **32 hoặc 64 [[luồng]]** thực thi cùng lúc trong [[GPU]] AMD.
- Giúp [[GPU]] **tăng tốc [[tính toán song song]]** trong các [[ứng dụng]] [[đồ họa]], [[AI]], và xử lý [[dữ liệu]] lớn.

### Cách hoạt động

**Trong kiến trúc GCN (Graphics Core Next) của AMD:**
- **1 wavefront = 64 [[luồng]]**.
- Chạy trên một đơn vị xử lý **Compute Unit (CU)**.

**Trong kiến trúc RDNA (Radeon DNA) của AMD:**
- **1 wavefront = 32 [[luồng]]** (giống [[Warp]] của NVIDIA).
- Tối ưu hóa cho game và đồ họa hiện đại.