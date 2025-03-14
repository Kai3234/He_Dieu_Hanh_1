Trong kiến trúc [[CUDA]] của NVIDIA (dùng trong [[GPU]]), warp là nhóm gồm 32 [[luồng]] được [[GPU]] xử lý cùng lúc.

Khi bạn lập trình với [[CUDA]], bạn thường làm việc với các [[khối luồng]]. Mỗi [[khối luồng]] được chia thành các warp, mỗi warp có 32 [[luồng]].

### Cách Warps hoạt động

- [[GPU]] không xử lý từng [[luồng]] riêng lẻ, mà xử lý theo nhóm warp.
- Mỗi warp có 32 [[luồng]] chạy đồng thời trên các [[lõi xử lý]] [[GPU]].
- Nếu một khối có 256 [[luồng]], nó sẽ được chia thành 256 / 32 = 8 warp.
- Các warp được thực thi theo kiểu [[SIMT]] → tức là tất cả các [[luồng]] trong một warp thực hiện cùng một [[lệnh]] nhưng trên các [[dữ liệu]] khác nhau.