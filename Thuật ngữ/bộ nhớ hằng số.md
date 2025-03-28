- [[Bộ nhớ]] hằng số (Constant Memory) là một vùng nhớ đặc biệt trong [[bộ nhớ toàn cục]] (Global Memory) của [[GPU]] ([[CUDA]]), được tối ưu cho truy cập đọc và thường dùng cho [[dữ liệu]] không thay đổi trong suốt quá trình thực thi [[kernel]].
- ### **Đặc điểm của [[bộ nhớ]] hằng số**
    - **Chỉ đọc (Read-Only)**: Các [[luồng]] chỉ có thể **đọc** [[dữ liệu]] từ [[bộ nhớ]] hằng số, còn **[[CPU]] mới có thể ghi** vào nó.  
    - **Tối ưu [[băng thông]]**: Nếu tất cả các [[luồng]] đọc cùng một giá trị, [[dữ liệu]] sẽ được **cache** hiệu quả, giúp giảm [[độ trễ]].  
    - **[[Dung lượng]] nhỏ (~64KB)**: Do được thiết kế để lưu các hằng số dùng chung, [[bộ nhớ]] này có [[dung lượng]] giới hạn. 
    - **Nhanh hơn Global Memory**: Vì có **[[bộ nhớ]] đệm (cache)** giúp giảm số lần truy cập [[DRAM]].
