Bố cục tuyến tính hóa của ma trận 2D, hay còn gọi là "flattening" hoặc "serialization", là quá trình chuyển đổi một ma trận hai chiều thành một mảng một chiều. Quá trình này rất quan trọng trong nhiều ứng dụng, đặc biệt là trong lĩnh vực [[xử lý ảnh]], học máy và lưu trữ dữ liệu.

Có hai cách phổ biến để tuyến tính hóa một ma trận M có kích thước m×n:

1. Tuyến tính hóa theo hàng (Row-major order)
	- Duyệt theo từng hàng, từ trái sang phải.
	- Nếu ma trận có kích thước m×n, phần tử M\[i]\[j] sẽ được lưu tại vị trí: 
		- index=i × n + j
2. Tuyến tính hóa theo cột (Column-major order)
	- Duyệt theo từng cột, từ trên xuống dưới.
	- Phần tử M\[i]\[j] sẽ được lưu tại vị trí: 
		- index=j×m+i