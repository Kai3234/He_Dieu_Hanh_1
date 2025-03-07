**Deadlock (Bế tắc)** là tình huống trong hệ thống máy tính hoặc [[lập trình]] [[đa luồng]] khi **hai hoặc nhiều [[tiến trình]]/ [[luồng]] (processes/threads)** bị "mắc kẹt" vì mỗi [[tiến trình]] đang giữ một tài nguyên và chờ đợi tài nguyên khác mà [[tiến trình]] kia đang nắm giữ. Kết quả là không [[tiến trình]] nào có thể tiếp tục thực thi, dẫn đến hệ thống "đóng băng".

### **Điều kiện để Deadlock xảy ra**

Deadlock chỉ xảy ra khi **cả 4 điều kiện sau cùng tồn tại**:

1. **Mutual Exclusion (Loại trừ tương hỗ)**:
    
    - Tài nguyên không thể chia sẻ (ví dụ: máy in, file đang ghi).
        
    - Chỉ một [[tiến trình]] được truy cập tài nguyên tại một thời điểm.
        
2. **Hold and Wait (Giữ và chờ)**:
    
    - [[Tiến trình]] đang giữ ít nhất một tài nguyên và chờ để nhận thêm tài nguyên khác.
        
3. **No Preemption (Không có ưu tiên giành giật)**:
    
    - Tài nguyên chỉ được giải phóng tự nguyện bởi [[tiến trình]] đang giữ nó.
        
4. **Circular Wait (Chờ vòng tròn)**:
    
    - Tồn tại một chuỗi các [[tiến trình]], mỗi [[tiến trình]] chờ tài nguyên mà [[tiến trình]] tiếp theo trong chuỗi đang giữ.