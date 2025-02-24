Một _thread_ là đơn vị thực thi nhỏ nhất có thể được quản lý bởi hệ điều hành. _Process_ là một nhóm các thread có liên kết, thực thi cùng nhau trên cùng một môi trường và cùng chia sẻ tài nguyên trên đó với nhau. Nghĩa là các thread trong cùng một process chia sẻ với nhau cùng một memory space và có thể giao tiếp trực tiếp với nhau.

Một thread không thể tồn tại bên ngoài một process. Ngoài ra, mỗi một thread chỉ có thể tồn tại trong một process.
Một thread còn có thể coi là một light-weight processes. Một _single-threaded process_ là một process chỉ tồn tại duy nhất một thread, một _multi-threaded process_ là một process có thể tồn tại một hoặc nhiều thread.

Thread được sử dụng chủ yếu để cải thiện ứng dụng thông qua việc tính toán song song (parallelism). Trên thực tế chỉ có một thread được thực thi tại một thời điểm bởi CPU, nhưng CPU có thể chuyển đổi nhanh chóng giữa các thread để tạo hiệu ứng giống như các thread đang được thực thi song song với nhau.