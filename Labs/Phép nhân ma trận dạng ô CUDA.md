# Mục tiêu
Triển khai một quy trình nhân ma trận dạng [[ô]] dày đặc bằng cách sử dụng [[bộ nhớ chia sẻ]]
# Điều kiện tiên quyết:
Trước khi bắt đầu phần lab này, đảm bảo:
- Đã hoàn thành Lab "Phép nhân ma trận"
- Đã hoàn thành các bài giảng module cần thiết

# Hướng dẫn
Chỉnh sửa code trong tab code để thực hiện các nhiệm vụ sau: 
- Cấp phát bộ nhớ thiết bị
- Sao chép bộ nhớ máy chủ sang thiết bị
- Khởi tạo kích thước [[khối luồng]] và lưới kernel
- Gọi kernel CUDA
- Sao chép kết quả từ thiết bị sang máy chủ
- Giải phóng bộ nhớ thiết bị
- Triển khai quy trình nhân ma trận sử dụng bộ nhớ chia sẻ và tiling
Các vị trí để chèn code được đánh dấu bằng //@@

# Hướng dẫn thiết lập cục bộ
Phiên bản mã nguồn gần đây nhất cho phòng thí nghiệm này cùng với các tập lệnh xây dựng có thể được tìm thấy trên kho lưu trữ Bitbucket. Mô tả về cách sử dụng công cụ CMake cùng với cách xây dựng phòng thí nghiệm để phát triển cục bộ có trong tài liệu README ở thư mục gốc của kho lưu trữ.

Tệp thực thi được tạo ra do quá trình biên dịch phòng thí nghiệm có thể được chạy bằng lệnh sau:

./TiledMatrixMultiplication_Template -e &lt;expected.raw> -i &lt;input0.raw>,&lt;input1.raw> -o &lt;output.raw>