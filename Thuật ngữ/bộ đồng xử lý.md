Bộ đồng xử lý (Coprocessor) là một [[bộ xử lý]] máy tính được sử dụng để bổ trợ chức năng cho [[CPU|bộ xử lý chính]]. Các tác vụ do bộ đồng xử lý thực hiện có thể bao gồm [[số học dấu phẩy động]], [[xử lý đồ họa]],[[ xử lý tín hiệu]], [[xử lý chuỗi]], [[mật mã học]] hoặc [[giao tiếp đầu vào, đầu ra|giao tiếp đầu vào/đầu ra (I/O)]] với [[thiết bị ngoại vi]]. Bằng cách chuyển các tác vụ đòi hỏi xử lý cao từ [[CPU]] sang, bộ đồng xử lý giúp tăng tốc hiệu suất hệ thống. Ngoài ra, bộ đồng xử lý cho phép tùy chỉnh các dòng máy tính, giúp khách hàng không có nhu cầu sử dụng hiệu năng bổ sung không phải trả thêm chi phí cho những tính năng không cần thiết.

### Chức năng

Các bộ đồng xử lý khác nhau về mức độ tự chủ của chúng. Một số phụ thuộc vào sự điều khiển trực tiếp thông qua các lệnh đồng xử lý được nhúng trong luồng lệnh của [[CPU]]. Những bộ khác là những [[bộ xử lý]] độc lập thực sự, có thể hoạt động không đồng bộ; tuy nhiên, chúng vẫn không được tối ưu hóa cho mã đa dụng hoặc không thể thực hiện được do [[kiến trúc tập lệnh]], chỉ tập trung vào việc tăng tốc các tác vụ cụ thể. Thông thường, các bộ đồng xử lý này được điều khiển thông qua [[truy cập bộ nhớ trực tiếp]], trong đó [[CPU|bộ xử lý chính]] xây dựng một danh sách lệnh. 

### Lợi ích chính:

- Tiết kiệm tài nguyên [[CPU]].
    
- Tăng tốc độ xử lý chuyên biệt.
    
- Linh hoạt trong thiết kế hệ thống.
### Ví dụ