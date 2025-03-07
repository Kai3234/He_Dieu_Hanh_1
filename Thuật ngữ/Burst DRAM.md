Burst DRAM (hay còn gọi là "burst mode DRAM") là một kỹ thuật được sử dụng trong bộ nhớ [[DRAM]] để tăng tốc độ [[truy cập dữ liệu]]. Nó cho phép bộ nhớ truyền một loạt [[dữ liệu]] liên tục (một "burst") mà không cần phải gửi địa chỉ cho mỗi lần truy cập.

Thay vì truy xuất từng ô nhớ riêng lẻ, Burst DRAM cho phép lấy nhiều [[ô|ô nhớ]] liên tiếp trong một lần yêu cầu, giúp tăng tốc độ truyền dữ liệu đáng kể.

## Cách thức hoạt động
- Khi [[CPU]] hoặc bộ điều khiển bộ nhớ yêu cầu dữ liệu từ [[bộ nhớ chính|RAM]], thay vì chỉ gửi 1 [[ô|ô nhớ]] mỗi lần, Burst DRAM có thể gửi một loạt (burst) dữ liệu liên tục.
- Điều này giúp giảm [[độ trễ truy cập bộ nhớ]] và cải thiện hiệu suất.
- Số lượng dữ liệu trong mỗi "burst" thường là 4, 8 hoặc 16 ô nhớ, tùy thuộc vào cấu hình của [[RAM]].