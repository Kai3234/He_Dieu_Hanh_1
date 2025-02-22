Đồng bộ hóa rào cản (Barrier Synchronization) là một kỹ thuật trong lập trình song song để đảm bảo tất cả các [[luồng (threads)]] trong một khối (block) hoàn thành một bước tính toán trước khi tiếp tục bước tiếp theo.
Trong lập trình GPU với CUDA, lệnh __ syncthreads() được sử dụng để thực hiện đồng bộ hóa rào cản trong mỗi [[khối luồng (thread block)]].
- Trong thuật toán song song, các luồng chạy độc lập và không phải lúc nào cũng hoàn thành cùng một lúc.
- Nếu một luồng truy cập dữ liệu trước khi dữ liệu đó được các luồng khác tải vào bộ nhớ chia sẻ, sẽ xảy ra lỗi đọc dữ liệu chưa hợp lệ hoặc race condition.
- Đồng bộ hóa rào cản giúp đảm bảo tất cả [[luồng (thread)]] đều chờ nhau hoàn tất một [[pha (phases)trước khi tiếp tục, tránh lỗi truy cập dữ liệu sai.