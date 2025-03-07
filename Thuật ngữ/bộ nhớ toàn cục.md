"Global memory" là một thuật ngữ thường được sử dụng trong lĩnh vực máy tính và lập trình, đặc biệt là trong ngữ cảnh của các hệ thống [[đa luồng]] hoặc [[lập trình song song]]. Nó thường chỉ đến một vùng nhớ mà tất cả các [[luồng]] hoặc [[tiến trình]] có thể truy cập. 

### Điểm chính về bộ nhớ toàn cục

1. **Truy cập chung**: Bộ nhớ toàn cục cho phép nhiều [[luồng]] hoặc tiến trình truy cập và chia sẻ dữ liệu. Điều này rất hữu ích trong các ứng dụng cần phối hợp giữa nhiều phần của [[chương trình]].
    
2. **Hiệu suất**: Mặc dù bộ nhớ toàn cục có thể dễ dàng [[chia sẻ dữ liệu]], việc truy cập vào nó có thể chậm hơn so với các loại bộ nhớ khác (như bộ nhớ cache hoặc bộ nhớ cục bộ) do độ trễ cao hơn.
    
3. **Quản lý đồng bộ**: Khi nhiều [[luồng]] hoặc tiến trình truy cập vào bộ nhớ toàn cục, cần có các cơ chế đồng bộ hóa để tránh xung đột và đảm bảo tính nhất quán của dữ liệu.
    
4. **Sử dụng trong GPU**: Trong lập trình [[GPU]], bộ nhớ toàn cục thường chỉ đến bộ nhớ mà tất cả các [[luồng]] có thể truy cập, và nó có thể ảnh hưởng đến hiệu suất của ứng dụng nếu không được quản lý đúng cách.