# Mục tiêu
Triển khai một thuật toán nhân ma trận vuông đặc. Các tối ưu hóa như chia ô (tiling) và sử dụng bộ nhớ chia sẻ không bắt buộc trong bài thực hành này.
# Yêu cầu trước
Trước khi bắt đầu bài thực hành, hãy đảm bảo rằng:
- Bạn đã hoàn thành bài thực hành _Cộng vector_
- Bạn đã hoàn thành các module giảng dạy cần thiết
# Hướng dẫn
Chỉnh sửa mã nguồn trong tab mã để thực hiện các bước sau:
- Cấp phát bộ nhớ trên thiết bị
- Sao chép bộ nhớ từ host sang thiết bị
- Khởi tạo kích thước luồng và lưới của kernel
- Gọi kernel CUDA
- Sao chép kết quả từ thiết bị về host
- Giải phóng bộ nhớ thiết bị
Hướng dẫn về vị trí cần đặt từng phần của mã được đánh dấu bằng các dòng chú thích `//@@`.
# Hướng dẫn cài đặt cục bộ 
Phiên bản mã nguồn mới nhất của bài thực hành này cùng với các tập lệnh biên dịch có thể được tìm thấy trong [Kho lưu trữ Bitbucket](#). Mô tả về cách sử dụng công cụ CMake cũng như cách xây dựng các bài thực hành để phát triển cục bộ có thể được tìm thấy trong tài liệu README tại thư mục gốc của kho lưu trữ.
Tệp thực thi được tạo ra sau khi biên dịch bài thực hành có thể được chạy bằng lệnh sau:
		./BasicMatrixMultiplication_Stream_Template -e <expected.raw> \
		    -i <input0.raw>,<input1.raw> -o <output.raw> -t matrix
Trong đó:
- `<expected.raw>` là đầu ra mong đợi,
- `<input0.raw>,<input1.raw>` là tập dữ liệu đầu vào,
- `<output.raw>` là đường dẫn tùy chọn để lưu kết quả.
Các tập dữ liệu có thể được tạo bằng trình tạo dữ liệu được biên dịch như một phần của quá trình biên dịch.
### Câu hỏi: 
1. **Có bao nhiêu phép toán số thực được thực hiện trong kernel nhân ma trận của bạn? Giải thích.**  
    **Trả lời:**  
    Số phép nhân vô hướng thực hiện là:  
    **numCRows * numCCols dot-products = 2 * numCRows * numCCols * numACols**
    
2. **Kernel của bạn thực hiện bao nhiêu lần đọc bộ nhớ toàn cục? Giải thích.**  
    **Trả lời:**  
    Số lần đọc bộ nhớ toàn cục:  
    **numCRows * numCCols dot-products = 2 * numCRows * numCCols * numACols**
    
3. **Kernel của bạn thực hiện bao nhiêu lần ghi bộ nhớ toàn cục? Giải thích.**  
    **Trả lời:**  
    **Chỉ có ma trận đầu ra được ghi. Số lần ghi bộ nhớ là numCRows * numCCols.**
    
4. **Mô tả một số tối ưu hóa có thể được áp dụng vào kernel của bạn để tăng tốc độ thực thi.**  
    **Trả lời:**  
    **Sử dụng kỹ thuật "tiling" để lưu trữ các ma trận đầu vào trong bộ nhớ chia sẻ nhằm giảm số lần truy xuất bộ nhớ toàn cục.**
    
5. **Kể tên ba ứng dụng của phép nhân ma trận.**  
    **Trả lời:**  
    **Phép nhân ma trận xuất hiện trong hầu hết các ứng dụng tính toán cường độ cao. Một số ứng dụng bao gồm: Mạng nơ-ron nhân tạo (Neural Networks), Đồ họa máy tính (Graphics), và Phương trình vi phân từng phần (PDEs).**
# Mẫu Code
Đoạn mã sau được đề xuất làm điểm khởi đầu cho sinh viên. Code này xử lý việc nhập, xuất dữ liệu cũng như kiểm tra kết quả. Sinh viên cần chèn mã của mình vào các phần được đánh dấu bằng `//@@`. Các phần code khác cần được giữ nguyên.
Tài liệu về thư viện **Lib GPUTK** có thể được tìm thấy trong [Kho lưu trữ Bitbucket](#) tại thư mục `"libgputk/docs"` trong thư mục gốc của kho lưu trữ.
```
#include <gputk.h>

#define gpuTKCheck(stmt) \
    do { \
        cudaError_t err = stmt; \
        if (err != cudaSuccess) { \
            gpuTKLog(ERROR, "Failed to run stmt ", #stmt); \
            gpuTKLog(ERROR, "Got CUDA error ... ", cudaGetErrorString(err)); \
            return -1; \
        } \
    } while (0)
    
// Tính toán C = A * B
__global__ void matrixMultiply(float *A, float *B, float *C, int numARows,
                               int numAColumns, int numBRows,
                               int numBColumns, int numCRows,
                               int numCColumns) {
    //@@ Chèn code để thực hiện phép nhân ma trận ở đây
}

int main(int argc, char **argv) {
    gpuTKArg_t args;
    float *hostA;  // Ma trận A
    float *hostB;  // Ma trận B
    float *hostC;  // Ma trận kết quả C
    float *deviceA;
    float *deviceB;
    float *deviceC;
    int numARows;     // Số hàng của ma trận A
    int numAColumns;  // Số cột của ma trận A
    int numBRows;     // Số hàng của ma trận B
    int numBColumns;  // Số cột của ma trận B
    int numCRows;     // Số hàng của ma trận C (bạn cần đặt giá trị này)
    int numCColumns;  // Số cột của ma trận C (bạn cần đặt giá trị này)

    args = gpuTKArg_read(argc, argv);

    gpuTKTime_start(Generic, "Importing data and creating memory on host"); //   Nhập dữ liệu và tạo bộ nhớ trên host
    hostA = (float *)gpuTKImport(gpuTKArg_getInputFile(args, 0), &numARows,
                                 &numAColumns);
    hostB = (float *)gpuTKImport(gpuTKArg_getInputFile(args, 1), &numBRows,
                                 &numBColumns);

    //@@ Đặt giá trị cho numCRows và numCColumns
    numCRows = 0;
    numCColumns = 0;

    //@@ Cấp phát bộ nhớ cho ma trận hostC
    gpuTKTime_stop(Generic, "Importing data and creating memory on host"); // Nhập dữ liệu và tạo bộ nhớ trên host

    gpuTKLog(TRACE, "The dimensions of A are ", numARows, " x ", numAColumns); // Kích thước của A
    gpuTKLog(TRACE, "The dimensions of B are ", numBRows, " x ", numBColumns); // Kích thước của B

    gpuTKTime_start(GPU, "Allocating GPU memory."); // Cấp phát bộ nhớ trên GPU
    //@@ Cấp phát bộ nhớ trên GPU ở đây
    gpuTKTime_stop(GPU, "Allocating GPU memory."); // Cấp phát bộ nhớ trên GPU

    gpuTKTime_start(GPU, "Copying input memory to the GPU."); // Sao chép dữ liệu đầu vào lên GPU
    //@@ Sao chép bộ nhớ lên GPU ở đây
    gpuTKTime_stop(GPU, "Copying input memory to the GPU."); // Sao chép dữ liệu đầu vào lên GPU

    //@@ Khởi tạo kích thước lưới và khối ở đây

    gpuTKTime_start(Compute, "Performing CUDA computation."); // Thực hiện tính toán CUDA
    //@@ Gọi kernel GPU ở đây

    cudaDeviceSynchronize();
    gpuTKTime_stop(Compute, "Performing CUDA computation"); // Thực hiện tính toán CUDA

    gpuTKTime_start(Copy, "Copying output memory to the CPU");  
    //@@ Sao chép bộ nhớ từ GPU về CPU ở đây  

    gpuTKTime_stop(Copy, "Copying output memory to the CPU");  

    gpuTKTime_start(GPU, "Freeing GPU Memory");  
    //@@ Giải phóng bộ nhớ GPU ở đây  

    gpuTKTime_stop(GPU, "Freeing GPU Memory");  

    gpuTKSolution(args, hostC, numCRows, numCColumns);  

    free(hostA);  
    free(hostB);  
    free(hostC);  

    return 0;  
}



```

#  Giải pháp mã: 
Sau đây là một triển khai khả thi của phòng thí nghiệm. Giải pháp này dành cho  
chỉ được sử dụng bởi đội ngũ giảng viên và không nên phân phát cho sinh viên.

	#include <gputk.h>
	// Tính toán C = A * B
	// Sgemm là viết tắt của phép nhân ma trận-ma trận tổng quát chính xác đơn
	__global__ void sgemm(float *A, float *B, float *C, int numARows,
						 int numAColumns, int numBRows, int numBColumns) {
		//@@ Chèn mã để thực hiện phép nhân ma trận ở đây
		int row = blockIdx.y * blockDim.y + threadIdx.y;
		int col = blockIdx.x * blockDim.x + threadIdx.x;
		if (row < numARows && col < numBColumns) {
		float sum = 0;
			for (int ii = 0; ii < numAColumns; ii++) {
				sum += A[row * numAColumns + ii] * B[ii * numBColumns + col];
			}
			C[row * numBColumns + col] = sum;
		}
	}
	#define gpuTKCheck(stmt)
		do {
			cudaError_t err = stmt;
			if (err != cudaSuccess) {
				gpuTKLog(ERROR, "Không chạy được stmt", #stmt);
				return -1;
			}
		} while (0)
	int main(int argc, char **argv) {
		gpuTKArg_t args;
		float *hostA; // Ma trận A
		float *hostB; // Ma trận B
		float *hostC; // Ma trận đầu ra C
		float *deviceA;
		float *deviceB;
		float *deviceC;
		int numARows; // số hàng trong ma trận A
		int numAColumns; // số cột trong ma trận A
		int numBRows; // số hàng trong ma trận B
		int numBColumns; // số cột trong ma trận A
		int numCRows;
		int numCColumns;
	
	args = gpuTKArg_read(argc, argv);
	
	gpuTKTime_start(Generic, "Nhập dữ liệu và tạo bộ nhớ trên máy chủ");
	hostA = (float *)gpuTKImport(gpuTKArg_getInputFile(args, 0), &numARows,
				&numAColumns);
	hostB = (float *)gpuTKImport(gpuTKArg_getInputFile(args, 1), &numBRows,
				&numBColumns);
	//Phân bổ ma trận hostC
	hostC = (float *)malloc(numARows * numBColumns * sizeof(float));
	 gpuTKTime_stop(Generic, "Nhập dữ liệu và tạo bộ nhớ trên máy chủ");
	 
	 numCRows = numARows;
	 numCColumns = numBColumns;
	 
	gpuTKLog(TRACE, "Kích thước của A là ", numARows, " x ", numAColumns);
	gpuTKLog(TRACE, "Kích thước của B là ", numBRows, " x ", numBColumns);
	gpuTKLog(TRACE, "Kích thước của C là ", numCRows, " x ", numCColumns);
	gpuTKTime_start(GPU, "Đang phân bổ bộ nhớ GPU.");
	//@@ Phân bổ bộ nhớ GPU tại đây
	gpuTKCheck(cudaMalloc((void **)&deviceA,
					numARows * numAColumns * sizeof(float)));
	gpuTKCheck(cudaMalloc((void **)&deviceB,
					numBRows * numBColumns * sizeof(float)));
	gpuTKCheck(cudaMalloc((void **)&deviceC,
					numARows * numBColumns * sizeof(float)));
	gpuTKTime_stop(GPU, "Phân bổ bộ nhớ GPU.");
	
	gpuTKTime_start(GPU, "Sao chép bộ nhớ đầu vào vào GPU.");
	//@@ Sao chép bộ nhớ vào GPU tại đây
	gpuTKCheck(cudaMemcpy(deviceA, hostA,
					numARows * numAColumns * sizeof(float),
					cudaMemcpyHostToDevice));
	gpuTKCheck(cudaMemcpy(deviceB, hostB,
					numBRows * numBColumns * sizeof(float),
					cudaMemcpyHostToDevice));
	gpuTKTime_stop(GPU, "Sao chép bộ nhớ đầu vào vào GPU.");
	
	//@@ Khởi tạo kích thước lưới và khối tại đây
	dim3 blockDim(16, 16);
	// đổi thành BColumns và ARows từ Acolumns và BRows
	
	0 code solution 6
	
	dim3 gridDim(ceil(((float)numBColumns) / blockDim.x),
	ceil(((float)numARows) / blockDim.y));
	
	gpuTKLog(TRACE, "Kích thước khối là ", blockDim.x, " x ", blockDim.y);
	gpuTKLog(TRACE, "Kích thước lưới là ", gridDim.x, " x ", gridDim.y);
	
	gpuTKTime_start(Compute, "Thực hiện tính toán CUDA");
	//@@ Khởi chạy GPU Kernel tại đây
	gpuTKCheck(cudaMemset(deviceC, 0, numARows * numBColumns * sizeof(float)));
	sgemm<<<gridDim, blockDim>>>(deviceA, deviceB, deviceC, numARows,
								numAColumns, numBRows, numBColumns);
	cudaDeviceSynchronize();
	gpuTKTime_stop(Compute, "Thực hiện tính toán CUDA");
	
	gpuTKTime_start(Copy, "Sao chép bộ nhớ đầu ra vào CPU");
	//@@ Sao chép bộ nhớ GPU trở lại CPU tại đây
	
	gpuTKCheck(cudaMemcpy(hostC, deviceC,
					numARows * numBColumns * sizeof(float),
					cudaMemcpyDeviceToHost));
	gpuTKTime_stop(Copy, "Sao chép bộ nhớ đầu ra vào CPU");
	
	gpuTKTime_start(GPU, "Giải phóng bộ nhớ GPU");
	//@@ Giải phóng bộ nhớ GPU tại đây
	cudaFree(deviceA);
	cudaFree(deviceB);
	cudaFree(deviceC);
	gpuTKTime_stop(GPU, "Giải phóng bộ nhớ GPU");
	
	gpuTKSolution(args, hostC, numARows, numBColumns);
	
	free(hostA);
	free(hostB);
	free(hostC);
	
	return 0;
	}
	

