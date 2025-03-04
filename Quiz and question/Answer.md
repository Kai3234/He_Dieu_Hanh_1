Câu 1. Giả sử một kernel được khởi động với 1000 khối [[luồng]], mỗi [[khối luồng|khối]] có 512 [[luồng]]. Nếu một biến được khai báo là biến [[bộ nhớ chia sẻ]], thì có bao nhiêu phiên bản của biến này sẽ được tạo ra trong suốt thời gian thực thi của kernel?
a.      1
==b.==      1,000
c.      512
d.      512,000  
**Giải thích:** Các biến bộ nhớ chia sẻ được phân bổ cho các [[khối luồng]]. Vì vậy, số lượng phiên bản là số lượng [[khối luồng]], tức là 1.000.
Câu 2. Đối với kernel nhân ma trận theo [[ô]], nếu chúng ta sử dụng [[ô]] kích thước 32x32, thì mức giảm sử dụng băng thông bộ nhớ cho các ma trận đầu vào A và B là bao nhiêu?
a. 1/8 mức sử dụng ban đầu  
b. 1/16 mức sử dụng ban đầu  
==c.== 1/32 mức sử dụng ban đầu  
d. 1/64 mức sử dụng ban đầu
**Giải thích:** Mỗi phần tử trong [[ô]] được sử dụng 32 lần, như đã giải thích trong bài giảng 4.3.
Câu 3. Đối với [[Kernel|kernel]] nhân ma trận đơn chính theo ô như đã trình bày trong [[4.4 Phép nhân ma trận dạng ô nhớ kernel|Bài giảng 4.4]], giả sử kích thước [[ô]] là 32x32 và hệ thống có kích thước burst DRAM là 128 byte. Sẽ có bao nhiêu burst DRAM được gửi đến bộ xử lý do việc tải một ô ma trận A bởi một [[khối luồng]]?
a.      16
==b.==      32
c.      64
d.      128
**Giải thích:** Đối với một [[ô]] A kích thước 32x32, mỗi hàng trong [[ô]] bao gồm 32 từ liên tiếp và được truy cập bởi một warp. Tổng lượng dữ liệu trong hàng chỉ là một burst duy nhất. Chúng ta có 32 hàng trong một [[ô]], vì vậy sẽ có 32 burst được gửi đến bộ xử lý.
Câu 4. Giả sử một nhân ma trận theo [[ô]] xử lý các điều kiện biên như đã giải thích trong  [[4.5 Xử lí kích thước ma trận bất kì trong thuật toán dạng ô]]. Giả sử chúng ta sử dụng [[ô]] kích thước 32x32 để xử lý các ma trận vuông có kích thước 1.000x1.000. Trong MỖI [[khối luồng]], số lượng warps tối đa sẽ có sự phân kỳ điều khiển do xử lý các điều kiện biên khi tải các [[ô]] A trong suốt quá trình thực thi của [[kernel]] là bao nhiêu?
==a.==      32
b.      24
c.      16
d.      8
**Giải thích:** Sự phân kỳ điều khiển xảy ra do việc xử lý cạnh bên phải. Đối với các [[khối luồng]] xử lý các [[ô]] hoàn toàn nằm trong phạm vi hợp lệ ở chiều y, tất cả 32 warps trong một khối sẽ trải qua sự phân kỳ tại ranh giới bên phải. Đối với các khối luồng xử lý các [[ô]] A ở dưới cùng trên cạnh bên phải, chỉ có 8 warps sẽ trải qua sự phân kỳ điều khiển vì tất cả các [[luồng]] trong 24 warps dưới sẽ không vượt qua bài kiểm tra ranh giới.