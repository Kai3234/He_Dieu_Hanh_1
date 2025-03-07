**Race Condition (Tranh chấp tài nguyên)** là một lỗi xảy ra khi **nhiều [[luồng]] (threads) hoặc [[tiến trình]] (processes)** cùng truy cập và thay đổi một **tài nguyên dùng chung** ([[biến]], [[tệp tin|file]], [[cơ sở dữ liệu]]) mà không được đồng bộ hóa. Kết quả của các thao tác này trở nên **không thể đoán trước**, phụ thuộc vào thứ tự thực thi của các [[luồng]], dẫn đến [[dữ liệu]] bị sai lệch hoặc hỏng.

### Nguyên nhân gây Race Condition

- **Không đồng bộ hóa**: Các [[luồng]] tự do truy cập tài nguyên chung mà không có [[cơ chế khóa]] (lock) hoặc kiểm soát.
    
- **[[Thao tác không nguyên tử]]**: Các phép toán như ghi/đọc dữ liệu bị chia cắt thành nhiều bước nhỏ, tạo cơ hội cho luồng khác can thiệp giữa chừng.