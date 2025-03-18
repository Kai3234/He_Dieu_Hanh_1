# Mã giải pháp
Sau đây là một triển khai khả thi của phòng thí nghiệm. Giải pháp này dành cho  
chỉ được sử dụng bởi đội ngũ giảng viên và không nên phân phát cho sinh viên.

 \#include <gputk.h>
 // Tính toán C = A * B
	// Sgemm là viết tắt của phép nhân ma trận-ma trận tổng quát chính xác đơn
```
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
	

