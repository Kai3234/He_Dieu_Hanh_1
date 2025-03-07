Tính toán song song (Parallel computing) là một hình thức tính toán trong đó nhiều phép tính hoặc [[tiến trình]] được thực hiện đồng thời. Nguyên tắc cơ bản của tính toán song song là chia một vấn đề lớn thành nhiều phần nhỏ hơn, sau đó giải quyết chúng song song, cùng một lúc.

### **Đặc điểm chính**:

1. **Chia để trị** (Divide and Conquer):  
    Bài toán được phân tách thành các tác vụ hoặc luồng (threads) độc lập hoặc phụ thuộc ít, xử lý đồng thời.
    
2. **Xử lý đồng thời**:  
    Các bộ xử lý (cores, máy tính, node) làm việc cùng lúc trên các phần khác nhau của bài toán.
    
3. **Kết hợp kết quả**:  
    Sau khi xử lý xong các phần, kết quả được tổng hợp để tạo ra đầu ra cuối cùng.