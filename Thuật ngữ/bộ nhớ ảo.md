**Bộ nhớ ảo (Virtual Memory)** là một kỹ thuật quản lý bộ nhớ của hệ điều hành, giúp chương trình có thể sử dụng nhiều [[bộ nhớ]] hơn lượng [[bộ nhớ chính|RAM]] thực có trên máy tính. Nó hoạt động bằng cách dùng một phần của ổ đĩa làm bộ nhớ tạm thời khi [[bộ nhớ chính|RAM]] đầy.

### Cách hoạt động của bộ nhớ ảo

Khi một chương trình yêu cầu nhiều bộ nhớ hơn dung lượng [[bộ nhớ chính|RAM]] hiện có:

1. [[hệ điều hành|Hệ điều hành]] tạm thời chuyển bớt dữ liệu từ [[bộ nhớ chính|RAM]] sang ổ đĩa.
2. [[dữ liệu|Dữ liệu]] này được lưu trong một file hoán đổi hoặc vùng swap trên ổ cứng/SSD.
3. Khi cần, [[dữ liệu]] này sẽ được đưa trở lại [[bộ nhớ chính|RAM]] để tiếp tục xử lý.