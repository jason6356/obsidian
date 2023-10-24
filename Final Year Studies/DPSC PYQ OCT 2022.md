![[Pasted image 20231023231736.png]]

- In p2p network, the system's performance can improve with a larger number of peers because each peer contributes to the network's resources.
- Peer can share the load by distributing data and processing tasks among themselves.

![[Pasted image 20231023232022.png]]

Concurrent access data without data synchronization

![[Pasted image 20231023233019.png]]

Yes

![[Pasted image 20231023233045.png]]

Yes, it is desirable and correct because that the two threads are not executed concurrently, instead thread 2 is waiting for thread 1 to done executing which prevents the data race
![[Pasted image 20231023233214.png]]

![[Pasted image 20231023233453.png]]

In this scenario where we have both setter method called concurrent which cause the data is not synchronized. In this scenario, even though the thread 1 does successfully executed the code, however the thread 2 would overwrite the value of the balance with the old balance which cause data inconsistency
![[Pasted image 20231023233723.png]]

```c++
std::mutex _mutex;
_mutex.lock();
balance = account.balance()
if (balance > 0.0) {
    if(balance > amount)
        accont.set(balance - amount);
}
_mutex.unlock();
```
![[Pasted image 20231023234003.png]]
Deadlock in the context of Inter-Process Communication (IPC) refers to a situation where two or more processes are unable to proceed because they are each waiting for the other(s) to release a resource that they need.
![[Pasted image 20231023234017.png]]

Semaphore1 : The threads need to contend for the semaphore token, therefore no data race
There is no deadlock because it uses only single semaphore

Semaphore2:
Data race, because each thread must content the semphore token twice, which enables them to access the criticial section simultanenously
There is a potential deadlock in this function because a single thread can acquire sem2 and get stuck in the sem2.acquire if other threads does no t release semaphore

Semaphore3
If multiple threads concurrently call `semaphore3`, they will release the semaphore token and immediately enter the critical section. There is a potential race condition, as multiple threads can access the critical section simultaneously.

Semaphore4
There is a potential for deadlock in this function if a thread acquires `sem4` and does not release it. This would block other threads from entering the critical section. Properly releasing the semaphore is essential to avoid deadlock.

![[Pasted image 20231023234624.png]]

**Undesirable Event**: Deadlock can occur if thread 1 and thread 2 both execute their tasks concurrently.

**Why**: Deadlock occurs because both `task1` and `task2` are designed to acquire `sem1` and `sem2`, but they do so in a different order. Thread 1 starts by acquiring `sem1`, while thread 2 starts by acquiring `sem2`. After acquiring the first semaphore, each task tries to acquire the other semaphore before entering the critical section. Since both threads have one of the semaphores, they will be blocked waiting for the other semaphore to be released.

**How It Can Happen**:

1. Thread 1 starts executing `task1` and acquires `sem1`.
2. Thread 2 starts executing `task2` and acquires `sem2`.
3. Thread 1 attempts to acquire `sem2`, but it is already held by thread 2, so thread 1 is blocked and cannot proceed.
4. Thread 2 tries to acquire `sem1`, but it is held by thread 1, so thread 2 is also blocked.
5. Now, both threads are waiting for the other to release the semaphore they need, resulting in a deadlock situation.
![[Pasted image 20231023234829.png]]
Read Write Condition
Write Read Condition
Write Write Condition
![[Pasted image 20231023234848.png]]

**S1 : a = 2 * x + y * y**
- Write Set (W1S1) : {a}
- Read Set (R1S1) : {x, y}

**S2: b = z % 7 + 1 << 6**
- Write Set (WS2) : {b}
- Read Set (RS2) : {z}

**S3: b = a << 7 | b & c**
- Write Set (WS3) : {b}
- Read Set (RS3) : {a, b, c}

**S1&S2**

- WS1 ∩ RS2 = {}
- WS2 ∩ RS1 = {}
- S1 and S2 does not have conflicts, they can execute in parallel

**S2&S3**
- WS2 ∩ RS3 = {b} , conflict
- WS3 ∩ RS2 = {} , no conflict
- S2 and S3 does have conflicts, they cannot execute in parallel

**S1&S3**
- WS1 ∩ RS3 = {a} , conflict
- WS3 ∩ RS1 = {}, no conflict
- S1 and S3 does have conflict, they cannot execute in parallel
![[Pasted image 20231023235751.png]]

 x = 5;
 y = x + 3;
 Instruction y = x +3 has true dependency on instruction x = 5 because instruction 2 reads the value of x which is written by instruction 1
![[Pasted image 20231023235940.png]]
- An anti-dependency, or Write-After-Read (WAR) dependency, occurs when an instruction writes to a variable that a later instruction reads.
1. x = 5;      // Instruction 1
2. y = x + 3;  // Instruction 2

- An output-dependency, or Write-After-Write (WAW) dependency, occurs when two instructions write to the same variable.

1. x = 5;      // Instruction 1
2. x = 7;      // Instruction 2

![[Pasted image 20231024000133.png]]

Anti-dependency = S1&S2
Output-dependency = S1&S3

![[Pasted image 20231024000212.png]]

```c++
// Original Instructions:
// S1: B = X * Z + sin(Y)^3
// S2: A = B * 9 - 10
// S3: B = 7

// Modified Instructions:
// Calculate B in parallel with other instructions
S1: B_temp = X * Z + sin(Y)^3

// Calculate A in parallel with B_temp (S1) and B (S3)
S2: A = B_temp * 9 - 10

// Assign B the value 7, ensuring no data dependencies with other instructions
S3: B = 7

```

![[Pasted image 20231024000609.png]]
```c++
// CUDA kernel for matrix multiplication
__global__ void matrixMultiplicationKernel(float* A, float* B, float* Result, int N) {
    // Calculate the row and column indices for the current thread
    int row = blockIdx.y * blockDim.y + threadIdx.y;
    int col = blockIdx.x * blockDim.x + threadIdx.x;

    if (row < N && col < N) {
        float sum = 0.0f;
        for (int i = 0; i < N; i++) {
            sum += A[row * N + i] * B[i * N + col];
        }
        Result[row * N + col] = sum;
    }
}

```
![[Pasted image 20231024000733.png]]

```c++
int N = ...; // Define the size of the square matrices (N x N)
int maxThreadsPerBlock = 1024; // Maximum number of threads per block supported by the GPU

// Calculate the number of blocks needed to cover the entire matrix
int numBlocksX = (N + maxThreadsPerBlock - 1) / maxThreadsPerBlock; // Ensure it's rounded up

// Define the grid and block dimensions using dim3
dim3 gridDimensions(numBlocksX, numBlocksX);
dim3 blockDimensions(maxThreadsPerBlock, maxThreadsPerBlock);

// Host call to the kernel function with the execution configuration
matrixMultiplicationKernel<<<gridDimensions, blockDimensions>>>(A, B, Result, N);

// Ensure proper error handling for the kernel call
cudaDeviceSynchronize();
cudaError_t cudaStatus = cudaGetLastError();
if (cudaStatus != cudaSuccess) {
    fprintf(stderr, "Kernel launch failed: %s\n", cudaGetErrorString(cudaStatus));
    // Handle the error appropriately
}

```
