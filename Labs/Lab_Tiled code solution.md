#include <gputk.h>
2
3 #define gpuTKCheck(stmt) \
4 do { \
5 cudaError_t err = stmt; \
6 if (err != cudaSuccess) { \
7 gpuTKLog(ERROR, "Failed to run stmt ", #stmt); \
8 return -1; \
9 } \
10 } while (0)
11
12 #define TILE_WIDTH 16
13
14 // Compute C = A * B
15 __global__ void matrixMultiply(float *A, float *B, float *C, int numARows,

0 code solution 5

16 int numAColumns, int numBRows,
17 int numBColumns, int numCRows,
18 int numCColumns) {
19 //@@ Insert code to implement matrix multiplication here
20 __shared__ float ds_M[TILE_WIDTH][TILE_WIDTH];
21 __shared__ float ds_N[TILE_WIDTH][TILE_WIDTH];
22 int bx = blockIdx.x, by = blockIdx.y, tx = threadIdx.x, ty = threadIdx.y,
23 Row = by * TILE_WIDTH + ty, Col = bx * TILE_WIDTH + tx;
24 float Pvalue = 0;
25
26 for (int m = 0; m < (numAColumns - 1) / TILE_WIDTH + 1; ++m) {
27 if (Row < numARows && m * TILE_WIDTH + tx < numAColumns)
28 ds_M[ty][tx] = A[Row * numAColumns + m * TILE_WIDTH + tx];
29 else
30 ds_M[ty][tx] = 0;
31 if (Col < numBColumns && m * TILE_WIDTH + ty < numBRows)
32 ds_N[ty][tx] = B[(m * TILE_WIDTH + ty) * numBColumns + Col];
33 else
34 ds_N[ty][tx] = 0;
35
36 __syncthreads();
37 for (int k = 0; k < TILE_WIDTH; ++k)
38 Pvalue += ds_M[ty][k] * ds_N[k][tx];
39 __syncthreads();
40 }
41 if (Row < numCRows && Col < numCColumns)
42 C[Row * numCColumns + Col] = Pvalue;
43 }
44
45 int main(int argc, char **argv) {
46 gpuTKArg_t args;
47 float *hostA; // The A matrix
48 float *hostB; // The B matrix
49 float *hostC; // The output C matrix
50 float *deviceA;
51 float *deviceB;
52 float *deviceC;
53 int numARows; // number of rows in the matrix A
54 int numAColumns; // number of columns in the matrix A
55 int numBRows; // number of rows in the matrix B
56 int numBColumns; // number of columns in the matrix B
57 int numCRows; // number of rows in the matrix C (you have to set this)
58 int numCColumns; // number of columns in the matrix C (you have to set
59 // this)
60
61 args = gpuTKArg_read(argc, argv);
62
63 gpuTKTime_start(Generic, "Importing data and creating memory on host");
64 hostA = (float *)gpuTKImport(gpuTKArg_getInputFile(args, 0), &numARows,
65 &numAColumns);
66 hostB = (float *)gpuTKImport(gpuTKArg_getInputFile(args, 1), &numBRows,
67 &numBColumns);
68 //@@ Set numCRows and numCColumns
69 numCRows = numARows;
70 numCColumns = numBColumns;
71 //@@ Allocate the hostC matrix

0 code solution 6
72 hostC = (float *)malloc(sizeof(float) * numCRows * numCColumns);
73 gpuTKTime_stop(Generic, "Importing data and creating memory on host");
74
75 gpuTKLog(TRACE, "The dimensions of A are ", numARows, " x ", numAColumns);
76 gpuTKLog(TRACE, "The dimensions of B are ", numBRows, " x ", numBColumns);
77
78 gpuTKTime_start(GPU, "Allocating GPU memory.");
79 //@@ Allocate GPU memory here
80 cudaMalloc(&deviceA, sizeof(float) * numARows * numAColumns);
81 cudaMalloc(&deviceB, sizeof(float) * numBRows * numBColumns);
82 cudaMalloc(&deviceC, sizeof(float) * numCRows * numCColumns);
83
84 gpuTKTime_stop(GPU, "Allocating GPU memory.");
85
86 gpuTKTime_start(GPU, "Copying input memory to the GPU.");
87 //@@ Copy memory to the GPU here
88 cudaMemcpy(deviceA, hostA, sizeof(float) * numARows * numAColumns,
89 cudaMemcpyHostToDevice);
90 cudaMemcpy(deviceB, hostB, sizeof(float) * numBRows * numBColumns,
91 cudaMemcpyHostToDevice);
92
93 gpuTKTime_stop(GPU, "Copying input memory to the GPU.");
94
95 //@@ Initialize the grid and block dimensions here
96 dim3 dimGrid((numCColumns - 1) / TILE_WIDTH + 1,
97 (numCRows - 1) / TILE_WIDTH + 1, 1);
98 dim3 dimBlock(TILE_WIDTH, TILE_WIDTH, 1);
99
100 gpuTKTime_start(Compute, "Performing CUDA computation");
101 //@@ Launch the GPU Kernel here
102 matrixMultiply<<<dimGrid, dimBlock>>>(
103 deviceA, deviceB, deviceC, numARows, numAColumns, numBRows,
104 numBColumns, numCRows, numCColumns);
105
106 cudaDeviceSynchronize();
107 gpuTKTime_stop(Compute, "Performing CUDA computation");
108
109 gpuTKTime_start(Copy, "Copying output memory to the CPU");
110 //@@ Copy the GPU memory back to the CPU here
111 cudaMemcpy(hostC, deviceC, sizeof(float) * numCRows * numCColumns,
112 cudaMemcpyDeviceToHost);
113
114 gpuTKTime_stop(Copy, "Copying output memory to the CPU");
115
116 gpuTKTime_start(GPU, "Freeing GPU Memory");
117 //@@ Free the GPU memory here
118 cudaFree(deviceA);
119 cudaFree(deviceB);
120 cudaFree(deviceC);
121
122 gpuTKTime_stop(GPU, "Freeing GPU Memory");
123
124 gpuTKSolution(args, hostC, numCRows, numCColumns);
125
126 free(hostA);
127 free(hostB);

0 code solution 7

128 free(hostC);
129
130 return 0;
131 }