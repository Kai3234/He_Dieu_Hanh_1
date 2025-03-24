- **[[Biến]] tự động (Automatic Variables)** là các [[biến]] được khai báo trong **hàm [[kernel]]**, có **phạm vi trong một [[luồng]] (thread)** và được lưu trữ trong **[[thanh ghi]] (registers)** hoặc **[[bộ nhớ cục bộ]] (local memory)**.
##### **Đặc điểm của [[Biến]] Tự Động**
1. **Phạm vi (Scope)**
    - Chỉ tồn tại trong **một [[luồng]] (thread)** và không thể chia sẻ với [[luồng]] khác.
    - Tự động bị hủy khi [[luồng]] kết thúc.
2. **Vị trí lưu trữ**
    - Mặc định, [[CUDA]] sẽ lưu trữ [[biến]] tự động trong **[[thanh ghi]] (registers)** để truy xuất nhanh.
    - Nếu [[biến]] quá lớn hoặc là mảng, nó sẽ được lưu trong **[[bộ nhớ cục bộ]] (local memory)**, tức là **[[bộ nhớ toàn cục]] (global memory)** thay vì [[thanh ghi]].
3. **[[Hiệu suất]]**
    - **Lưu trữ trong [[thanh ghi]] nhanh nhất** nhưng số lượng [[thanh ghi]] có hạn.
    - **Lưu trữ trong [[bộ nhớ cục bộ]] có [[độ trễ]] cao hơn**, vì nó thực chất nằm trong [[bộ nhớ toàn cục]].