# Mục tiêu
Triển khai một quy trình nhân ma trận dạng [[ô]] dày đặc bằng cách sử dụng [[bộ nhớ chia sẻ]]
# Điều kiện tiên quyết:
Trước khi bắt đầu phần lab này, đảm bảo:
- Đã hoàn thành Lab "Phép nhân ma trận"
- Đã hoàn thành các bài giảng module cần thiết

# Hướng dẫn
Chỉnh sửa code trong tab code để thực hiện các nhiệm vụ sau: 
- Cấp phát bộ nhớ thiết bị
- Sao chép bộ nhớ máy chủ sang thiết bị
- Khởi tạo kích thước [[khối luồng]] và lưới kernel
- Gọi kernel [[CUDA]]
- Sao chép kết quả từ thiết bị sang máy chủ
- Giải phóng bộ nhớ thiết bị
- Triển khai quy trình nhân ma trận sử dụng [[bộ nhớ chia sẻ]]  và [[Tiling|tiling]]
Các vị trí để chèn code được đánh dấu bằng //@@

# Hướng dẫn thiết lập cục bộ
Phiên bản mã nguồn gần đây nhất cho phòng thí nghiệm này cùng với các tập lệnh xây dựng có thể được tìm thấy trên kho lưu trữ [Bitbucket](https://bitbucket.org/nvidia-dli/gputeachingkit-labs/). Mô tả về cách sử dụng công cụ CMake cùng với cách xây dựng lab để phát triển cục bộ có trong tài liệu README ở thư mục gốc của kho lưu trữ.

Tệp thực thi được tạo ra do quá trình biên dịch lab có thể được chạy bằng lệnh sau:

./TiledMatrixMultiplication_Template -e &lt;expected.raw> -i &lt;input0.raw>,&lt;input1.raw> -o &lt;output.raw>

Trong đó &lt;expected.raw> là đầu ra dự kiến, &lt;input0.raw>,&lt;input1.raw> là tập dữ liệu đầu vào và &lt;output.raw> là đường dẫn tùy chọn để lưu trữ kết quả. Các tập dữ liệu có thể được tạo bằng trình tạo tập dữ liệu được xây dựng như một phần của quy trình biên dịch.

## Câu hỏi
1. Có bao nhiêu phép toán dấu phẩy động đang được thực hiện trong kernel nhân ma trận của bạn? Giải thích.
   Trả lời: Một tích vô hướng trên mỗi phần tử ma trận đầu ra. 2 * numACols * numCRows * numCCols
2. Có bao nhiêu lần đọc [[bộ nhớ toàn cục]] đang được thực hiện bởi kernel của bạn? Giải thích.
   Trả lời: Mỗi luồng thực hiện 2 * ceil(numACols/TILE_WIDTH) và có numCRows * numCCols luồng hoạt động.
3. Có bao nhiêu lần ghi [[bộ nhớ toàn cục]] đang được thực hiện bởi kernel của bạn? Giải thích.
   Trả lời: Chỉ có ma trận đầu ra được ghi. numCRows * numCCols
4. Mô tả những tối ưu hóa nào khác có thể được triển khai cho kernel của bạn để tăng tốc độ hiệu suất.
   Trả lời: Điều chỉnh các tham số khởi chạy [[kernel]] để có độ chiếm dụng tối ưu.
5. So sánh độ khó triển khai của kernel này so với MP trước đó. Bạn gặp khó khăn gì với việc triển khai này?
   Trả lời: Dịch chỉ mục địa chỉ từ [[bộ nhớ toàn cục|không gian toàn cục]] sang không gian [[bộ nhớ chia sẻ]] là một nơi mới để mắc lỗi.
6. Giả sử bạn có các ma trận có kích thước lớn hơn kích thước [[luồng|luồng]] tối đa. Phác thảo một thuật toán sẽ thực hiện thuật toán nhân ma trận sẽ thực hiện phép nhân trong trường hợp này.
   Trả lời: Mỗi [[luồng|luồng]] có thể thực hiện 4 hoặc 9 hoặc 16 phần tử liền kề của ma trận (làm thô luồng).
7. Giả sử bạn có các ma trận không vừa với [[bộ nhớ toàn cục]]. Phác thảo một thuật toán sẽ thực hiện thuật toán nhân ma trận sẽ thực hiện phép nhân ngoài vị trí.
   Trả lời: Giống như đầu vào được xếp gạch cho [[bộ nhớ chia sẻ]], đầu vào có thể được xếp gạch ở phía máy chủ để thực thi kernel.

# Mẫu mã
Mã sau được đề xuất làm điểm khởi đầu cho sinh viên. Sinh viên dự kiến sẽ chèn mã của mình vào các phần được phân định bằng //@@. Sinh viên dự kiến sẽ giữ nguyên mã khác. Tài liệu về thư viện Lib GPUTK có thể được tìm thấy trên kho lưu trữ Bitbucket trong thư mục "libgputk/docs" ở thư mục gốc của kho lưu trữ.

\#include <gputk.h>

\#define gpuTKCheck(stmt) 

	do { 
	
		cudaError_t err = stmt; 
		
		if (err != cudaSuccess) { 
		
		gpuTKLog(ERROR, "Không chạy được stmt", #stmt); 
		
		gpuTKLog(ERROR, "Đã nhận lỗi CUDA ", cudaGetErrorString(err)); 
		
		return -1; 
		} 
	} while (0)
	
	// Tính toán C=A∗B
	
	__global__ void matrixMultiplyShared(float *A, float *B, float *C, int numARows, int numAColumns, int numBRows, int numBColumns, int numCRows, int numCColumns) {
	//@@ Chèn mã để triển khai phép nhân ma trận tại đây
	//@@ Bạn phải sử dụng bộ nhớ chia sẻ cho lab này
	}
	
	int main(int argc, char **argv) {
		gpuTKArg_t args;
		float *hostA; // Ma trận A
		float *hostB; // Ma trận B
		float *hostC; // Ma trận đầu ra C
		float *deviceA;
		float *deviceB;
		float *deviceC;
		int numARows; // Số hàng trong ma trận A
		
		int numAColumns; // Số cột trong ma trận A
		
		int numBRows; // Số hàng trong ma trận B
		
		int numBColumns; // Số cột trong ma trận B
		
		int numCRows; // Số hàng trong ma trận C (bạn phải đặt giá trị này)
		
		int numCColumns; // Số cột trong ma trận C (bạn phải đặt giá trị này)
		
		args = gpuTKArg_read(argc, argv);
		
		gpuTKTime_start(Generic, "Đang nhập dữ liệu và tạo bộ nhớ trên máy chủ");
		
		hostA = (float *)gpuTKImport(gpuTKArg_getInputFile(args, 0), &numARows, &numAColumns);
		
		hostB = (float *)gpuTKImport(gpuTKArg_getInputFile(args, 1), &numBRows, &numBColumns);
		
		//@@ Đặt numCRows và numCColumns
		
		numCRows = 0;
		
		numCColumns = 0;
		
		//@@ Cấp phát ma trận hostC
		
		gpuTKTime_stop(Generic, "Đang nhập dữ liệu và tạo bộ nhớ trên máy chủ");
		
		gpuTKLog(TRACE, "Kích thước của A là %d x %d", numARows, numAColumns);
		
		gpuTKLog(TRACE, "Kích thước của B là %d x %d", numBRows, numBColumns);
		
		gpuTKTime_start(GPU, "Đang cấp phát bộ nhớ GPU.");
		
		//@@ Cấp phát bộ nhớ GPU tại đây
		
		gpuTKTime_stop(GPU, "Đang cấp phát bộ nhớ GPU.");
		
		gpuTKTime_start(GPU, "Sao chép bộ nhớ đầu vào vào GPU.");
		
		//@@ Sao chép bộ nhớ vào GPU tại đây
		
		gpuTKTime_stop(GPU, "Sao chép bộ nhớ đầu vào vào GPU.");
		
		//@@ Khởi tạo kích thước lưới và khối tại đây
		
		gpuTKTime_start(Compute, "Thực hiện tính toán CUDA");
		
		//@@ Khởi chạy GPU Kernel tại đây
		
		cudaDeviceSynchronize();
		
		gpuTKTime_stop(Compute, "Thực hiện tính toán CUDA");
		
		gpuTKTime_start(Copy, "Sao chép bộ nhớ đầu ra vào CPU");
		
		//@@ Sao chép bộ nhớ GPU trở lại CPU tại đây
		
		gpuTKTime_stop(Copy, "Sao chép bộ nhớ đầu ra vào CPU");
		
		gpuTKTime_start(GPU, "Giải phóng bộ nhớ GPU");
		
		//@@ Giải phóng bộ nhớ GPU tại đây
		
		gpuTKTime_stop(GPU, "Giải phóng bộ nhớ GPU");
		
		gpuTKSolution(args, hostC, numCRows, numCColumns);
		
		free(hostA);
		free(hostB);
		free(hostC);
		
		return 0;
	}
# Giải pháp mã
Sau đây là một triển khai khả thi của phòng thí nghiệm. Giải pháp này dành cho  
chỉ được sử dụng bởi đội ngũ giảng viên và không nên phân phát cho sinh viên.

\#include <gputk.h>
\#include <gputk.h>

\#define gpuTKCheck(stmt) 

	do { 
	
		cudaError_t err = stmt; 
		
		if (err != cudaSuccess) { 
		
		gpuTKLog(ERROR, "Không chạy được stmt", #stmt); 
		
		gpuTKLog(ERROR, "Đã nhận lỗi CUDA ", cudaGetErrorString(err)); 
		
		return -1; 
		} 
	} while (0)
	
	// Tính toán C=A∗B
	
	__global__ void matrixMultiplyShared(float *A, float *B, float *C, int numARows, int numAColumns, int numBRows, int numBColumns, int numCRows, int numCColumns) {
	//@@ Chèn mã để triển khai phép nhân ma trận tại đây
	//@@ Bạn phải sử dụng bộ nhớ chia sẻ cho lab này
	}
	
	int main(int argc, char **argv) {
		gpuTKArg_t args;
		float *hostA; // Ma trận A
		float *hostB; // Ma trận B
		float *hostC; // Ma trận đầu ra C
		float *deviceA;
		float *deviceB;
		float *deviceC;
		int numARows; // Số hàng trong ma trận A
		
		int numAColumns; // Số cột trong ma trận A
		
		int numBRows; // Số hàng trong ma trận B
		
		int numBColumns; // Số cột trong ma trận B
		
		int numCRows; // Số hàng trong ma trận C (bạn phải đặt giá trị này)
		
		int numCColumns; // Số cột trong ma trận C (bạn phải đặt giá trị này)
		
		args = gpuTKArg_read(argc, argv);
		
		gpuTKTime_start(Generic, "Đang nhập dữ liệu và tạo bộ nhớ trên máy chủ");
		
		hostA = (float *)gpuTKImport(gpuTKArg_getInputFile(args, 0), &numARows, &numAColumns);
		
		hostB = (float *)gpuTKImport(gpuTKArg_getInputFile(args, 1), &numBRows, &numBColumns);
		
		//@@ Đặt numCRows và numCColumns
		
		numCRows = 0;
		
		numCColumns = 0;
		
		//@@ Cấp phát ma trận hostC
		
		gpuTKTime_stop(Generic, "Đang nhập dữ liệu và tạo bộ nhớ trên máy chủ");
		
		gpuTKLog(TRACE, "Kích thước của A là %d x %d", numARows, numAColumns);
		
		gpuTKLog(TRACE, "Kích thước của B là %d x %d", numBRows, numBColumns);
		
		gpuTKTime_start(GPU, "Đang cấp phát bộ nhớ GPU.");
		
		//@@ Cấp phát bộ nhớ GPU tại đây
		
		gpuTKTime_stop(GPU, "Đang cấp phát bộ nhớ GPU.");
		
		gpuTKTime_start(GPU, "Sao chép bộ nhớ đầu vào vào GPU.");
		
		//@@ Sao chép bộ nhớ vào GPU tại đây
		
		gpuTKTime_stop(GPU, "Sao chép bộ nhớ đầu vào vào GPU.");
		
		//@@ Khởi tạo kích thước lưới và khối tại đây
		
		gpuTKTime_start(Compute, "Thực hiện tính toán CUDA");
		
		//@@ Khởi chạy GPU Kernel tại đây
		
		cudaDeviceSynchronize();
		
		gpuTKTime_stop(Compute, "Thực hiện tính toán CUDA");
		
		gpuTKTime_start(Copy, "Sao chép bộ nhớ đầu ra vào CPU");
		
		//@@ Sao chép bộ nhớ GPU trở lại CPU tại đây
		
		gpuTKTime_stop(Copy, "Sao chép bộ nhớ đầu ra vào CPU");
		
		gpuTKTime_start(GPU, "Giải phóng bộ nhớ GPU");
		
		//@@ Giải phóng bộ nhớ GPU tại đây
		
		gpuTKTime_stop(GPU, "Giải phóng bộ nhớ GPU");
		
		gpuTKSolution(args, hostC, numCRows, numCColumns);
		
		free(hostA);
		free(hostB);
		free(hostC);
		
		return 0;
	}

















































	
	
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
	//@@ Free the GPU memory here
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
	
