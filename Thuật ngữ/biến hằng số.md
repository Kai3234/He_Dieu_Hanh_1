- **[[Biến]] hằng số (Constant Memory)** là một vùng **[[bộ nhớ]] chỉ đọc**, được tối ưu để **tất cả các [[luồng]] trong [[lưới]] (grid) có thể truy cập nhanh** khi cần sử dụng [[dữ liệu]] chung.
##### **Đặc điểm của [[Biến]] Hằng Số (Constant Memory)**
1. **Phạm vi (Scope)**
    - **Tương tự [[bộ nhớ toàn cục]]**, nhưng được [[tối ưu hóa]] hơn cho **truy cập đọc**.
    - Tất cả các **[[luồng]] trong [[lưới]] (grid)** có thể [[đọc dữ liệu]] từ [[bộ nhớ hằng số]].
2. **Thời gian tồn tại**
    - **Suốt vòng đời của [[ứng dụng]] (Application lifetime)**, nghĩa là [[dữ liệu]] không bị mất đi trong quá trình thực thi [[kernel]].
3. **Tính chất chỉ đọc (Read-only)**
    - **Chỉ có một bản duy nhất** của [[biến]] hằng số trong toàn bộ **[[lưới]] (grid)**.
    - Các **[[luồng]] chỉ có thể đọc**, không thể ghi vào **[[bộ nhớ hằng số]]**.
    - **Chỉ có thể được khởi tạo từ [[CPU]] (host)**, không thể thay đổi bên trong [[kernel]].
4. **Ưu điểm**
    - [[Truy cập bộ nhớ]] nhanh hơn so với [[bộ nhớ toàn cục]].
    - Tối ưu [[hiệu suất]] khi nhiều [[luồng]] cần dùng chung một [[dữ liệu]].