Câu 1. Giả sử một kernel được khởi động với 1000 khối [[luồng]], mỗi [[khối luồng]] có 512 [[luồng]]. Nếu một biến được khai báo là biến bộ nhớ chia sẻ, thì có bao nhiêu phiên bản của biến này sẽ được tạo ra trong suốt thời gian thực thi của kernel?
a.      1
b.      1,000
c.      512
d.      512,000
Câu 2. Đối với kernel nhân ma trận theo ô, nếu chúng ta sử dụng ô kích thước 32x32, thì mức giảm sử dụng băng thông bộ nhớ cho các ma trận đầu vào A và B là bao nhiêu?
a. 1/8 mức sử dụng ban đầu  
b. 1/16 mức sử dụng ban đầu  
c. 1/32 mức sử dụng ban đầu  
d. 1/64 mức sử dụng ban đầu
Câu 3. Đối với kernel nhân ma trận đơn chính theo ô như đã trình bày trong Bài giảng 4.4, giả sử kích thước ô là 32x32 và hệ thống có kích thước burst DRAM là 128 byte. Sẽ có bao nhiêu burst DRAM được gửi đến bộ xử lý do việc tải một ô ma trận A bởi một khối luồng?
a.      16
b.      32
c.      64
d.      128
Câu 4. Giả sử một nhân ma trận theo ô xử lý các điều kiện biên như đã giải thích trong Bài giảng 4.5. Giả sử chúng ta sử dụng ô kích thước 32x32 để xử lý các ma trận vuông có kích thước 1.000x1.000. Trong MỖI khối luồng, số lượng warps tối đa sẽ có sự phân kỳ điều khiển do xử lý các điều kiện biên khi tải các ô A trong suốt quá trình thực thi của kernel là bao nhiêu?
a.      32
b.      24
c.      16
d.      8
