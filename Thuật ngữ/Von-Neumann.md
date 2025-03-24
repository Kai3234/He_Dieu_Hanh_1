**Kiến trúc Von Neumann** là một mô hình [[kiến trúc máy tính]] được đề xuất bởi nhà toán học John von Neumann vào năm 1945. Đây là một trong những khái niệm nền tảng quan trọng nhất trong lịch sử phát triển [[máy tính]].

Các đặc điểm chính của kiến trúc Von Neumann:

1. [[bộ nhớ dùng chung]]: Cả [[chương trình]] ([[lệnh]]) và [[dữ liệu]] đều được lưu trữ trong cùng một [[bộ nhớ]] vật lý. Điều này khác biệt so với kiến trúc Harvard, nơi [[bộ nhớ]] [[chương trình]] và [[bộ nhớ]] [[dữ liệu]] được tách biệt.
    
2. **[[CPU]] với hai thành phần chính**:
    
    - Đơn vị điều khiển (Control Unit): Trích xuất [[lệnh]] từ [[bộ nhớ]] và điều khiển quá trình thực thi
    - Đơn vị tính toán ([[ALU]] - Arithmetic Logic Unit): Thực hiện các phép tính số học và logic
3. **Mô hình tuần tự**: Thực thi [[lệnh]] theo trình tự một cách tuần tự với chu kỳ "lấy [[lệnh]] - [[giải mã]] - thực thi" (fetch-decode-execute cycle)
    
4. **Bus [[dữ liệu]]**: Sử dụng một kênh truyền dẫn (bus) để di chuyển [[dữ liệu]] giữa các thành phần khác nhau
    
5. **Đơn [[luồng]]**: Về cơ bản là kiến trúc xử lý đơn [[luồng]], mỗi thời điểm thực hiện một [[lệnh]]
    
6. **Nút thắt cổ chai Von Neumann**: Kiến trúc này đối mặt với hạn chế gọi là "Von Neumann bottleneck" - nút thắt cổ chai khi [[CPU]] phải liên tục chờ đợi để nhận [[dữ liệu]] và [[lệnh]] từ [[bộ nhớ]] qua một kênh truyền duy nhất.
    

Hầu hết các [[máy tính]] hiện đại vẫn dựa trên nguyên lý cơ bản của kiến trúc Von Neumann, mặc dù đã có nhiều cải tiến như [[bộ nhớ]] cache, xử lý pipeline, xử lý song song, và kiến trúc siêu vô hướng để giảm thiểu các hạn chế của mô hình gốc.

[[GPU]] khác với kiến trúc Von Neumann truyền thống ở chỗ nó được thiết kế theo hướng xử lý song song quy mô lớn, với hàng nghìn [[lõi xử lý]] nhỏ thay vì một vài lõi mạnh như [[CPU]].