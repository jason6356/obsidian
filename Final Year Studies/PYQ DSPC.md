![[Pasted image 20231023173701.png]]

| Aspect | Race Condition | Dead Locks |
| --- | --- | --- |
| Definition | Concurrent access to shared data without synchronization, leading to inconsistent updates. | Threads or processes are stuck in a circular wait, rendering the program unresponsive. |
| Occurrence | In multithreaded programs when shared data isn't properly synchronized. | In multithreaded/multiprocesses app when resource like locks or I/O devices are contested. |

![[Pasted image 20231023174411.png]]

Implement locking mechanisms, such as mutexes (mutual exclusion), to restrict access to shared resources. A lock ensures that only one thread can access the resource at a time.
![[Pasted image 20231023174532.png]]

No, because we are using mutex for synchronization

![[Pasted image 20231023175457.png]]

![[Pasted image 20231023175513.png]]

In this scenario, thread1 locks mtx1, and thread2 also locks mtx1.
thread1 proceeds to lock mtx2, and thread2 is blocked, waiting for mtx2
thread1 continues executing, manipulating resource2
After thread1 unlocks mtx2, thread2 acquires mtx2 and continue executing, manipulating resource1

![[Pasted image 20231023180624.png]]

![[Pasted image 20231023180612.png]]
![[Pasted image 20231023180633.png]]
```c++
std::mutex mtx1;
std::mutex mtx2;

void thread1(){
    mtx1.lock();
    std::this_thread::sleep_for(std::chrono::milliseconds(1)); // Simulate work
    mtx2.lock();
    resource1.manipulate();
    resource2.manipulate();
    mtx2.unlock();
    mtx1.unlock();
}

void thread2(){
    mtx1.lock(); // Acquire mtx1 before mtx2
    mtx2.lock();
    resource1.manipulate();
    resource2.manipulate();
    mtx2.unlock();
    mtx1.unlock();
}

```

1. Both threads acquire `mtx1` before `mtx2`. This order ensures that there is no circular wait condition and eliminates the possibility of a deadlock.
    
2. I've added a small delay using `std::this_thread::sleep_for` in `thread1` to simulate some work within the threads, which can help demonstrate the effectiveness of the locking order in preventing a deadlock.
![[Pasted image 20231023180804.png]]

Mutex `mtx1` is locked first, followed by `mtx2`. When the mutexes are released, they are unlocked in the reverse order: `mtx2` is unlocked before `mtx1`.

This release order is crucial for avoiding a deadlock. Deadlocks occur when multiple threads are waiting for resources in a circular wait pattern, which means that they're each holding resources and waiting for others to release the resources they need. By releasing the mutexes in reverse order, you break the circular wait pattern and prevent the possibility of a deadlock. Both `thread1` and `thread2` release `mtx2` before releasing `mtx1`, which ensures that the resources can be acquired in the same order they were acquired originally.
![[Pasted image 20231023181020.png]]

In concurrent programming, a critical section is a designated portion of code where shared resources are accessed and potentially modified. It ensures that only one thread or process can execute this section at a time, preventing race conditions and data corruption.

![[Pasted image 20231023181315.png]]

The token holder has privilege to access to the resources
![[Pasted image 20231023181333.png]]

Token ownership in token passing algorithms grants a process or node the exclusive right to access a shared resource. The entity holding the token is the only one allowed to enter the critical section and utilize the resource.

![[Pasted image 20231023181423.png]]
**Outdated Request**: An outdated request is a request made by a process or node that was valid at the time it was initiated but has lost its relevance or cannot be fulfilled due to subsequent events or changes in the system.
![[Pasted image 20231023191202.png]]

All sites first would check whether the request is outdated, since all the site has the same, we can conclude that when we are checking with the request queue in each of the site is [5,3,4,2,7], on request (5,8), we would check on index 5, which is 7 from the request field, since 7 is less than 8, then it is not an outdated request, next up is we would update the queue for all sites which from [5,3,4,2,7] to [5,3,4,2,8]

![[Pasted image 20231023191354.png]]
[6,3,5,2,8]
![[Pasted image 20231023191428.png]]
Site 5 first check for index 4 in his request queue, which is 2, since 2 is more than 1, then its a outdated request, therefore it would not be updated since its an outdated request

![[Pasted image 20231023191528.png]]

Site 2 would compare the sequence number in the message, which means that site 2 would first process the message first, first it compares the sequence number, the following message is (5,8) 8 is the sequence number, and inside the request queue, it is 7 since 7 is less than 8 therefore it is not an outdated request, therefore it would process the request update the token to [5,3,4,2,8]. then sends the token to site 5. Therefore the content of token is [5,3,4,2,8].
![[Pasted image 20231023192247.png]]

Yes, the token would be [6,3,4,2,7] when site 2 pass to site 1.
![[Pasted image 20231023193446.png]]

Death Lock avoidance
![[Pasted image 20231023193500.png]]

[10,5,7] - [(2 + 3 + 2), (1 + 1), (2 + 1 + 2)] = [10,5,7] - [7,2,5] = [3,3,2]
![[Pasted image 20231023193630.png]]
P0 = [7,5,3] - [0,1,0] = 7 4 3
P1 = [3,2,2] - [2,0,0] = 1 2 2
P2 = [9,0,2] - [3,0,2] = 6 0 2
P3 = [2,2,2] - [2,1,1] = 0 1 1
P4 = [4,3,3] - [0,0,2] = 4 3 1

![[Pasted image 20231023193817.png]]

Need <= work => work = work + allocation

P0,   7 4 3 <= 3 3 2 , not
P1,   1 2 2 <= 3 3 2 , yes then 
3 3 2 + 2 0 0  = 5 3 2

P2, 6 0 0 <= 5 3 2 , Not
P3, 0 1 1 <= 5 3 2, yes then 
5 3 2 + 2 1 1  = 7 4 3

P4, 4 3 3 <= 743, yes then

7 4 3 + 0 0 2 = 7 4 5

P0, 7 4 3 <= 7 5 5 , yes then
7 5 5 + 0 1 0 = 7 5 5

P2, 6 0 2 <= 7 5 5, yes then 
7 5 5 + 3 0 2 = 10 5 7

<P1, P3, P4, P0, P2>

![[Pasted image 20231023194448.png]]

0 1 1 <= 3 3 2 yes then
3 3 2 + 2 1 1  = 5 3 3

4 3 1 <= 5 3 3 yes then
5 3 3 + 0 0 2 = 5 3 5

6 0 2 <= 5 3 5, no then its a dead lock

There will be a dead lock when the process reach through P2, we don't have enough resource for P2 if we use this sequence
![[Pasted image 20231023195333.png]]

```c++
#include <stdio.h>
#include <omp.h>

void parallel_add(int* num_array, int N) {
    int stage = 0;
    
    while (N > 1) {
        #pragma omp parallel for
        for (int i = 0; i < N / 2; i++) {
            int idx = 2 * i + 1;
            num_array[idx] += num_array[idx - 1];
        }

        // If N is odd, the last element should be included in the next stage
        if (N % 2 == 1) {
            num_array[N - 1] = num_array[N - 2];
        }

        // Update N for the next stage
        N = (N + 1) / 2;
        stage++;
    }

    printf("Parallel prefix sum completed in %d stages.\n", stage);
}

int main() {
    int N = 8;
    int num_array[] = {1, 2, 3, 4, 5, 6, 7, 8};

    parallel_add(num_array, N);

    // Print the result
    for (int i = 0; i < N; i++) {
        printf("%d ", num_array[i]);
    }
    printf("\n");

    return 0;
}



```


![[Pasted image 20231023195931.png]]

Read Write Condition
Write Read Condition
Write Write Condition
![[Pasted image 20231023195924.png]]
**S1 : p = y * x + y / k**
- Write Set (WS1): {p}
- Read Set (RS1): {y, x, k}

**S2: q = 7 >> 1 & 0xfff | y**
- Write Set (WS2): {q}
- Read Set (RS2): {y}

**S3: q = p ^ ~q | k && c**
- Write Set (WS3): {q}
- Read Set (RS3): {p, q, k, c}


1. **Possible Parallel Execution of S1 and S2**:
   - WS1 ∩ RS2 = {} (No intersection)
   - WS2 ∩ RS1 = {} (No intersection)
   - S1 and S2 do not have conflicts. They can be executed in parallel.

2. **Possible Parallel Execution of S2 and S3**:
   - WS2 ∩ RS3 = {q} (Intersection: S2 writes q, and S3 reads q)
   - WS3 ∩ RS2 = {q} (Intersection: S3 writes q, and S2 reads q)
   - S2 and S3 have a conflict due to the shared variable q. Parallel execution is not possible between S2 and S3.

3. **Possible Parallel Execution of S1 and S3**:
   - WS1 ∩ RS3 = {q} (Intersection: S1 writes q, and S3 reads q)
   - WS3 ∩ RS1 = {q} (Intersection: S3 writes q, and S1 reads q)
   - S1 and S3 have a conflict due to the shared variable q. Parallel execution is not possible between S1 and S3.

To summarize:
- S1 and S2 can be executed in parallel.
- S2 and S3 have a conflict, so parallel execution between them is not possible.
- S1 and S3 also have a conflict, so parallel execution between them is not possible.

