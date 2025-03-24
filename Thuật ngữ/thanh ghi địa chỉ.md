- **[[Thanh ghi]] địa chỉ (Address Register - AR)** là một loại [[thanh ghi]] trong **[[bộ xử lý]] ([[CPU]]/[[GPU]])**, có nhiệm vụ **lưu trữ địa chỉ [[bộ nhớ]]** của [[dữ liệu]] hoặc [[lệnh]] cần truy cập.
##### **Các loại [[thanh ghi]] địa chỉ trong [[CPU]]**
1. **Memory Address Register (MAR)**
    - Chứa địa chỉ của ô nhớ mà [[CPU]] muốn truy xuất.
    - Khi [[CPU]] muốn [[đọc dữ liệu]] từ [[RAM]], địa chỉ này được đặt vào MAR.
2. **Stack Pointer (SP)**
    - Chứa địa chỉ của đỉnh ngăn xếp (Stack).
    - Dùng trong quản lý hàm đệ quy và gọi hàm.
3. **Instruction Pointer (IP) hoặc Program Counter (PC)**
    - Lưu địa chỉ của [[lệnh]] tiếp theo sẽ được thực thi.
    - Tự động tăng sau mỗi [[lệnh]] để [[CPU]] chạy tuần tự.
##### **[[Thanh ghi]] địa chỉ trong [[GPU]] & [[CUDA]]**
- Trong **[[GPU]] ([[CUDA]])**, mỗi **[[luồng]] (thread)** có thể cần truy cập đến [[bộ nhớ toàn cục]] (Global Memory) hoặc [[bộ nhớ chia sẻ]] (Shared Memory).
- Để tăng [[hiệu suất]], [[CUDA]] sử dụng **các [[thanh ghi]] địa chỉ** giúp quản lý [[truy cập bộ nhớ]] hiệu quả hơn.
- **Nếu không tối ưu tốt**, các [[truy cập bộ nhớ]] không được sắp xếp hợp lý sẽ gây ra **memory divergence**, làm giảm tốc độ xử lý.