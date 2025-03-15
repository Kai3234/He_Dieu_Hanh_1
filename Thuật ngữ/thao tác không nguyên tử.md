**Thao tác không nguyên tử (non-atomic operation)** là một thao tác trong [[lập trình]] hoặc hệ thống [[máy tính]] mà **không đảm bảo tính toàn vẹn** trong quá trình thực hiện. Điều này có nghĩa là thao tác có thể bị **gián đoạn** hoặc **chia nhỏ** thành nhiều bước, dẫn đến khả năng xảy ra **xung đột** hoặc **lỗi** khi có nhiều [[tiến trình]] (process) hoặc [[luồng]] (thread) cùng truy cập và thay đổi [[dữ liệu]].

---

### Đặc điểm của thao tác không nguyên tử:

1. **Có thể bị gián đoạn:** Thao tác không nguyên tử có thể bị ngắt giữa chừng bởi [[hệ điều hành]] hoặc các [[luồng]] khác.
    
2. **Không đảm bảo tính nhất quán:** Khi nhiều [[luồng]] cùng thực hiện thao tác không nguyên tử trên cùng một [[dữ liệu]], kết quả có thể không như mong đợi do xung đột.
    
3. **Dễ gây ra lỗi:** Các lỗi như **[[race condition]]** (tình trạng đua nhau) thường xảy ra với thao tác không nguyên tử.