**Luồng (Thread)** là đơn vị nhỏ nhất của [[mã lệnh]] có thể được **[[lập lịch]] và thực thi độc lập** bởi [[hệ điều hành]]. Một [[tiến trình]] (process) có thể chứa nhiều [[luồng]], và các luồng này **chia sẻ tài nguyên** ([[bộ nhớ]], [[tệp tin|file]], [[dữ liệu]]) với nhau để thực hiện các tác vụ đồng thời. Luồng giúp tận dụng tối đa tài nguyên [[CPU]] và cải thiện hiệu suất [[ứng dụng]].

### Đặc điểm chính của luồng
- **Chia sẻ tài nguyên**:
    - Các luồng trong cùng [[tiến trình]] dùng chung [[bộ nhớ toàn cục]].
- **Nhẹ (Lightweight)**:
    - Tạo/xóa luồng nhanh hơn [[tiến trình]], tốn ít tài nguyên hệ thống.
- **Độc lập thực thi**:
    - Mỗi luồng có **[[ngăn xếp]] (stack)** riêng để lưu [[biến cục bộ]] và trạng thái.
