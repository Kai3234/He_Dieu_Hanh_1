- **[[Biến]] cục bộ** là [[biến]] được khai báo bên trong một **hàm, [[khối lệnh]] hoặc [[luồng]] (thread)**, chỉ có hiệu lực trong phạm vi đó và bị hủy ngay sau khi kết thúc phạm vi hoạt động.
##### **Đặc điểm của [[biến]] cục bộ**
1. **Phạm vi (Scope):**
    - Chỉ tồn tại trong hàm hoặc [[khối lệnh]] mà nó được khai báo.
    - Các phần khác của [[chương trình]] không thể truy cập [[biến]] này.
2. **Thời gian tồn tại (Lifetime):**
    - [[Biến]] chỉ tồn tại trong **thời gian thực thi của [[luồng]] (thread) hoặc hàm**.
    - Khi hàm hoặc [[luồng]] kết thúc, [[biến]] sẽ bị **giải phóng khỏi [[bộ nhớ]]**.
3. **Loại [[bộ nhớ]] trong [[CUDA]]:**
    - [[Biến]] cục bộ **thường được lưu trong [[thanh ghi]] (register)** nếu có thể.
    - Nếu [[biến]] là một **mảng (array)**, nó sẽ được lưu trong **[[bộ nhớ toàn cục]] (Global Memory)** thay vì [[thanh ghi]].