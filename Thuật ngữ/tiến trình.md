Một tiến trình có thể hiểu là một thể hiện (instance) của một [[chương trình]] đang được thực thi. Mỗi tiến trình có không gian [[bộ nhớ]] riêng, tài nguyên riêng và được quản lý độc lập bởi [[hệ điều hành]].

### Các đặc điểm chính của tiến trình:

1. **Không gian [[bộ nhớ]] riêng**: Mỗi tiến trình có vùng nhớ riêng, không chia sẻ trực tiếp với các tiến trình khác.
    
2. **Tài nguyên riêng**: Mỗi tiến trình sở hữu các tài nguyên như file, socket, [[bộ nhớ]], [[CPU]] time, v.v.
    
3. **Độc lập**: Các tiến trình chạy độc lập với nhau. Nếu một tiến trình bị lỗi, nó thường không ảnh hưởng đến các tiến trình khác.
    
4. **[[Đa luồng]] (Multithreading)**: Một tiến trình có thể chứa nhiều [[luồng]] (threads) để thực hiện các tác vụ song song.