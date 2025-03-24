- [[Thanh ghi]] [[lệnh]] (Instruction Register - IR) là một loại [[thanh ghi]] trong [[bộ xử lý]] ([[CPU]]/[[GPU]]), có nhiệm vụ lưu trữ [[lệnh]] hiện tại đang được [[CPU]]/[[GPU]] [[giải mã]] và thực thi.
##### **Chức năng của [[thanh ghi]] [[lệnh]]**
1. **Lưu trữ [[lệnh]] đang thực thi**: Khi một [[lệnh]] được lấy từ [[bộ nhớ]] ([[RAM]]) vào [[CPU]], [[lệnh]] đó được lưu tạm thời trong **IR** trước khi được [[giải mã]] và thực thi.
2. **Trung gian giữa [[bộ nhớ]] và [[CPU]]**: Giúp [[CPU]] xử lý từng [[lệnh]] mà không cần truy cập lại vào [[bộ nhớ]] liên tục.
3. **Tăng tốc độ thực thi**: Vì [[lệnh]] được lưu ngay trong [[CPU]], giúp giảm thời gian truy xuất [[bộ nhớ]].
##### **Cách [[thanh ghi]] [[lệnh]] hoạt động**
1. **Fetch (Nạp [[lệnh]])**:
    - [[CPU]] lấy [[lệnh]] từ [[bộ nhớ]] **(Program Counter - PC chứa địa chỉ [[lệnh]] tiếp theo)**.
    - [[Lệnh]] này được lưu vào **IR**.
2. **Decode ([[Giải mã]] [[lệnh]])**:
    - [[CPU]] [[giải mã]] [[lệnh]] trong **IR** để xác định loại [[lệnh]] và toán hạng.
3. **Execute (Thực thi [[lệnh]])**:
    - [[CPU]] thực hiện [[lệnh]] và cập nhật kết quả vào [[thanh ghi]] hoặc [[bộ nhớ]].
##### **[[Thanh ghi]] [[lệnh]] trong [[GPU]] & [[CUDA]]**
- **Trong [[GPU]] ([[CUDA]])**, mỗi **[[Warp]]** (nhóm 32 [[luồng]]) thường thực thi cùng một [[lệnh]].
- [[GPU]] có **Instruction Buffer**, tương tự [[thanh ghi]] [[lệnh]], để quản lý các [[lệnh]] đang thực thi.
- Nếu các [[luồng]] trong một [[Warp]] thực thi các nhánh điều kiện khác nhau (**Divergent Branching**), [[hiệu suất]] có thể giảm do các [[luồng]] phải chờ nhau.