- **[[Thanh ghi]] [[dữ liệu]] (Data Register - DR)** là một loại **[[thanh ghi]] (register)** trong [[CPU]] hoặc [[GPU]], được sử dụng để **lưu trữ tạm thời [[dữ liệu]]** khi thực hiện các phép toán hoặc truyền [[dữ liệu]] giữa các thành phần của [[bộ xử lý]].
##### **Chức năng của [[thanh ghi]] [[dữ liệu]]**
1. **[[Lưu trữ dữ liệu]] tạm thời** trước khi được xử lý hoặc ghi vào [[bộ nhớ]].
2. **Trung gian giữa [[CPU]] và [[bộ nhớ]]**: Khi [[CPU]] [[đọc dữ liệu]] từ [[RAM]] hoặc từ một [[thiết bị ngoại vi]], [[dữ liệu]] này sẽ được lưu vào [[thanh ghi]] [[dữ liệu]] trước khi xử lý.
3. **Tăng tốc độ xử lý**: Vì [[thanh ghi]] nằm trong [[CPU]], tốc độ truy xuất nhanh hơn nhiều so với [[RAM]].
##### **Phân loại [[thanh ghi]] [[dữ liệu]]**
Trong [[CPU]], [[thanh ghi]] [[dữ liệu]] có thể bao gồm:
- **General-Purpose Registers (GPRs)**: [[Thanh ghi]] đa dụng, có thể chứa [[dữ liệu]] số nguyên hoặc địa chỉ.
- **Floating-Point Registers (FPRs)**: [[Lưu trữ dữ liệu]] [[dấu phẩy động]].
- **Accumulator (AC)**: [[Thanh ghi]] tích lũy, thường dùng trong các phép toán số học.
- **Memory Data Register (MDR)**: Dùng để chứa [[dữ liệu]] đọc/ghi giữa [[bộ nhớ]] và [[CPU]].
##### **[[Thanh ghi]] [[dữ liệu]] trong [[GPU]] & [[CUDA]]**
- Trong **[[GPU]] ([[CUDA]])**, mỗi [[luồng]] (thread) có một tập **[[thanh ghi]] [[dữ liệu]] riêng** để lưu trữ [[biến cục bộ]].
- **Nếu số [[thanh ghi]] bị dùng quá nhiều**, [[dữ liệu]] sẽ bị đẩy xuống **local memory** (chậm hơn), gây ra **register spilling** và giảm [[hiệu suất]].
