Bộ đồng xử lý (Coprocessor) là một [[bộ xử lý]] máy tính được sử dụng để bổ trợ chức năng cho [[CPU|bộ xử lý chính]]. Các tác vụ do bộ đồng xử lý thực hiện có thể bao gồm [[số học dấu phẩy động]], [[xử lý đồ họa]],[[ xử lý tín hiệu]], [[xử lý chuỗi]], [[mật mã học]] hoặc [[giao tiếp đầu vào, đầu ra|giao tiếp đầu vào/đầu ra (I/O)]] với [[thiết bị ngoại vi]]. Bằng cách chuyển các tác vụ đòi hỏi xử lý cao từ [[CPU]] sang, bộ đồng xử lý giúp tăng tốc hiệu suất hệ thống. Ngoài ra, bộ đồng xử lý cho phép tùy chỉnh các dòng máy tính, giúp khách hàng không có nhu cầu sử dụng hiệu năng bổ sung không phải trả thêm chi phí cho những tính năng không cần thiết.

### Chức năng

Các bộ đồng xử lý khác nhau về mức độ tự chủ. Một số phụ thuộc vào việc điều khiển trực tiếp thông qua các [[lệnh đồng xử lý]], được nhúng trong luồng lệnh của [[CPU]]. Những bộ khác hoạt động như các bộ xử lý độc lập, có khả năng xử lý không đồng bộ; tuy nhiên, chúng không được tối ưu hóa cho các tác vụ tổng quát hoặc không thể thực hiện do [[kiến trúc tập lệnh]] hạn chế, chuyên tập trung vào việc tăng tốc các nhiệm vụ cụ thể. Thông thường, các bộ đồng xử lý này được điều khiển bằng [[truy cập bộ nhớ trực tiếp]], với bộ xử lý chủ ([[CPU]]) xây dựng một danh sách lệnh để hướng dẫn hoạt động của chúng.

### Lợi ích chính:

- Tiết kiệm tài nguyên [[CPU]].
    
- Tăng tốc độ xử lý chuyên biệt.
    
- Linh hoạt trong thiết kế hệ thống.
### Ví dụ về các loại bộ đồng xử lý

- **[[FPU]] (Floating Point Unit)** – Xử lý phép toán dấu phẩy động, tăng tốc các phép toán toán học phức tạp.
- **[[GPU]] (Graphics Processing Unit)** – Xử lý đồ họa, tăng tốc hiển thị hình ảnh, video và AI.
- **[[DSP]] (Digital Signal Processor)** – Xử lý tín hiệu số, ứng dụng trong âm thanh, hình ảnh, viễn thông.
- **TPU (Tensor Processing Unit)** – Đồng xử lý chuyên dụng cho AI/Machine Learning của Google.
- **Bộ đồng xử lý mã hóa (Encryption Coprocessor)** – Hỗ trợ mã hóa, giải mã dữ liệu bảo mật.