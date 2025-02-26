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
Phiên bản mã nguồn gần đây nhất cho phòng thí nghiệm này cùng với các tập lệnh xây dựng có thể được tìm thấy trên kho lưu trữ [Bitbucket](https://bitbucket.org/nvidia-dli/gputeachingkit-labs/). Mô tả về cách sử dụng công cụ CMake cùng với cách xây dựng phòng thí nghiệm để phát triển cục bộ có trong tài liệu README ở thư mục gốc của kho lưu trữ.

Tệp thực thi được tạo ra do quá trình biên dịch lab có thể được chạy bằng lệnh sau:

./TiledMatrixMultiplication_Template -e &lt;expected.raw> -i &lt;input0.raw>,&lt;input1.raw> -o &lt;output.raw>

Trong đó &lt;expected.raw> là đầu ra dự kiến, &lt;input0.raw>,&lt;input1.raw> là tập dữ liệu đầu vào và &lt;output.raw> là đường dẫn tùy chọn để lưu trữ kết quả. Các tập dữ liệu có thể được tạo bằng trình tạo tập dữ liệu được xây dựng như một phần của quy trình biên dịch.

## Câu hỏi
1. Có bao nhiêu phép toán dấu phẩy động đang được thực hiện trong kernel nhân ma trận của bạn? Giải thích.
   Trả lời: Một tích vô hướng trên mỗi phần tử ma trận đầu ra. 2 * numACols * numCRows * numCCols
2. Có bao nhiêu lần đọc [[bộ nhớ toàn cục]] đang được thực hiện bởi kernel của bạn? Giải thích.
   Trả lời: Mỗi luồng thực hiện 2 * ceil(numACols/TILE_WIDTH) và có numCRows * numCCols luồng hoạt động.
3. Có bao nhiêu lần ghi [[bộ nhớ toàn cục]] đang được thực hiện bởi kernel của bạn? Giải thích.
   Trả lời: Chỉ có ma trận đầu ra được ghi. numCRows * numCCols
4. Mô tả những tối ưu hóa nào khác có thể được triển khai cho kernel của bạn để tăng tốc độ hiệu suất.
   Trả lời: Điều chỉnh các tham số khởi chạy kernel để có độ chiếm dụng tối ưu.
5. So sánh độ khó triển khai của kernel này so với MP trước đó. Bạn gặp khó khăn gì với việc triển khai này?
   Trả lời: Dịch chỉ mục địa chỉ từ không gian toàn cục sang không gian bộ nhớ chia sẻ là một nơi mới để mắc lỗi.
6. Giả sử bạn có các ma trận có kích thước lớn hơn kích thước [[luồng (thread)|luồng]] tối đa. Phác thảo một thuật toán sẽ thực hiện thuật toán nhân ma trận sẽ thực hiện phép nhân trong trường hợp này.
   Trả lời: Mỗi [[luồng (thread)|luồng]] có thể thực hiện 4 hoặc 9 hoặc 16 phần tử liền kề của ma trận (làm thô luồng).
7. Giả sử bạn có các ma trận không vừa với bộ nhớ toàn cục. Phác thảo một thuật toán sẽ thực hiện thuật toán nhân ma trận sẽ thực hiện phép nhân ngoài vị trí.
   Trả lời: Giống như đầu vào được xếp gạch cho [[bộ nhớ chia sẻ]], đầu vào có thể được xếp gạch ở phía máy chủ để thực thi kernel.

# Mẫu mã