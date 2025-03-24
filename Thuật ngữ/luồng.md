**Luồng (Thread)** là một [[đơn vị xử lý]] nhỏ nhất trong một [[tiến trình]] (process), có khả năng thực thi độc lập và chia sẻ tài nguyên (như [[bộ nhớ]], [[tệp tin|file]], [[dữ liệu]]) với các luồng khác cùng thuộc một [[tiến trình]].

### Đặc điểm chính của luồng
- **Chia sẻ tài nguyên**:
    - Các luồng trong cùng [[tiến trình]] dùng chung [[bộ nhớ toàn cục]].
- **Nhẹ (Lightweight)**:
    - Tạo/xóa luồng nhanh hơn [[tiến trình]], tốn ít tài nguyên hệ thống.
- **Độc lập thực thi**:
    - Mỗi luồng có **ngăn xếp (stack)** riêng để lưu [[biến cục bộ của luồng|biến cục bộ]] và trạng thái.
