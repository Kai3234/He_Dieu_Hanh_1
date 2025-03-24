- **[[Khối]] [[lệnh]]** là một tập hợp các **câu [[lệnh]]** được nhóm lại với nhau và được bao bọc bởi **cặp dấu ngoặc nhọn `{}`**. Các [[lệnh]] trong [[khối]] sẽ được thực thi tuần tự theo thứ tự xuất hiện.
##### **Đặc điểm của [[khối]] [[lệnh]]**
1. **Được bao bởi `{}`**:
    - Tất cả các [[lệnh]] bên trong `{}` được coi là một **[[khối]] duy nhất**.
2. **Có phạm vi riêng (Scope)**:
    - Các [[biến]] khai báo trong [[khối]] [[lệnh]] chỉ có hiệu lực trong [[khối]] đó.
    - Khi ra khỏi [[khối]], [[biến]] sẽ bị hủy.
3. **Có thể dùng trong nhiều ngữ cảnh**:
    - Trong **hàm**.
    - Trong **cấu trúc điều kiện** (`if`, `else`).
    - Trong **vòng lặp** (`for`, `while`).
    - Trong **hàm lambda hoặc [[đa luồng]] ([[CUDA]], OpenMP, etc.)**.