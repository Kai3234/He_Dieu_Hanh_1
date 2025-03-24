- Trong [[lập trình]] **[[CUDA]]**, **Lưới (Grid)** là **tập hợp các [[khối]] (Blocks)**, trong đó mỗi [[khối]] chứa **nhiều [[luồng]] (Threads)**. Lưới giúp **tổ chức và quản lý việc thực thi song song** của hàng nghìn [[luồng]] trên [[GPU]].
##### **Đặc điểm của Lưới (Grid)**
1. **Cấu trúc của Lưới**
    - **Lưới bao gồm nhiều [[khối]] (Blocks)**, mỗi [[khối]] lại chứa nhiều [[luồng]] (Threads).
    - **Mỗi [[kernel]] khi được gọi sẽ chạy trên một lưới gồm nhiều [[khối]].*
2. **Kích thước của Lưới**
    - Một lưới có thể **1D (1 chiều), 2D (2 chiều) hoặc 3D (3 chiều)**, tùy vào bài toán cần xử lý.
    - [[CUDA]] cung cấp [[biến]] **gridDim** để xác định số lượng [[khối]] trong lưới.
3. **Mỗi [[khối]] trong lưới có ID riêng**
    - **blockIdx**: [[Biến]] **blockIdx.x, blockIdx.y, blockIdx.z** dùng để xác định chỉ số của từng [[khối]] trong lưới.
4. **[[Luồng]] trong [[khối]] cũng có ID riêng**
    - **threadIdx**: Xác định vị trí của một [[luồng]] trong một [[khối]].
    - **blockDim**: Xác định kích thước (số [[luồng]]) trong một [[khối]].