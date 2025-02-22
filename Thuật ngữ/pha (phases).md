Trong thuật toán nhân ma trận dạng ô, pha (phases) là các bước nhỏ trong quá trình tính toán, giúp giảm số lần truy xuất bộ nhớ toàn cục và tận dụng bộ nhớ chia sẻ để tối ưu hiệu suất.
Thay vì để mỗi [[luồng (thread)]] truy xuất toàn bộ dữ liệu từ bộ nhớ toàn cục trong một lần, thuật toán chia nhỏ quá trình xử lý thành nhiều pha:
1. Mỗi pha tải một phần dữ liệu nhỏ (tile) từ bộ nhớ toàn cục vào bộ nhớ chia sẻ.
2. Dữ liệu trong bộ nhớ chia sẻ được sử dụng để tính toán trong một pha.
3. Sau khi hoàn tất một pha, thuật toán tiếp tục tải dữ liệu mới cho pha tiếp theo.
Mỗi pha gồm 2 bước chính:
1. Tải dữ liệu: Các [[luồng (thread)]] cùng nhau nạp một ô dữ liệu vào bộ nhớ chia sẻ.
2. 
