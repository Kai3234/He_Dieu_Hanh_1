Bộ nhớ đệm (**Cache memory**) là một thành phần [[phần cứng]] hoặc [[phần mềm]] dùng để [[lưu trữ dữ liệu]], giúp các yêu cầu [[truy cập dữ liệu]] trong tương lai được xử lý nhanh hơn. [[dữ liệu|Dữ liệu]] được lưu trữ trong bộ nhớ đệm có thể là kết quả của một phép tính trước đó hoặc bản sao của [[dữ liệu]] được lưu trữ ở một nơi khác.

### Cơ chế hoạt động
Khi [[bộ xử lý]] cần truy cập dữ liệu, nó sẽ kiểm tra **bộ nhớ đệm trước**.
**Cache hit** xảy ra khi [[dữ liệu]] được yêu cầu có sẵn trong bộ nhớ đệm, trong khi **cache miss** xảy ra khi dữ liệu không có sẵn. Khi xảy ra cache hit, dữ liệu được truy xuất trực tiếp từ bộ nhớ đệm, giúp tăng tốc độ xử lý so với việc phải tính toán lại hoặc đọc từ [[bộ nhớ]] chậm hơn. Do đó, càng nhiều yêu cầu được xử lý từ bộ nhớ đệm, hệ thống sẽ hoạt động càng nhanh.

### Chức năng của bộ nhớ đệm
- Giảm thời gian truy xuất dữ liệu bằng cách lưu trữ các thông tin hay được sử dụng.
- Hạn chế việc truy cập [[bộ nhớ chính]] hoặc [[ổ cứng]], giúp tăng hiệu suất hệ thống.
- Cải thiện tốc độ xử lý của [[CPU]], [[ổ cứng]], [[trình duyệt web]] và [[ứng dụng]].