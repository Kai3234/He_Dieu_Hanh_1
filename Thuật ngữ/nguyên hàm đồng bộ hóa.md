**Nguyên hàm đồng bộ hóa (Synchronized Primitive or Synchronization Primitive)** là một khái niệm trong [[lập trình]] [[đa luồng]] (multithreading), dùng để đảm bảo rằng các [[luồng]] (threads) có thể truy cập tài nguyên chung một cách an toàn mà không xảy ra xung đột [[dữ liệu]].

## **Các phương pháp đồng bộ hóa phổ biến**

1. **Mutex (Mutual Exclusion – Loại trừ lẫn nhau)**
    
    - Chỉ cho phép một [[luồng]] truy cập tài nguyên tại một thời điểm.
    - Khi một [[luồng]] chiếm dụng Mutex, các [[luồng]] khác phải chờ.
2. **Semaphore**
    
    - Giới hạn số lượng [[luồng]] có thể truy cập tài nguyên cùng lúc.
    - Ví dụ: Giả sử có 5 ghế trong thư viện, tối đa 5 người có thể ngồi, ai đến sau phải chờ ghế trống.
3. **Spinlock**
    
    - Một loại khóa bận (busy-wait lock) cho phép [[luồng]] liên tục kiểm tra quyền truy cập thay vì đi vào trạng thái chờ.
    - Hiệu quả trong các hệ thống có [[độ trễ]] truy cập thấp.
4. **Monitor (Hoặc synchronized trong Java, lock trong Python)**
    
    - Gói gọn [[cơ chế khóa]] và điều phối [[luồng]] một cách tiện lợi.
    - Trong Java, từ khóa `synchronized` đảm bảo chỉ một [[luồng]] thực thi phương thức tại một thời điểm.