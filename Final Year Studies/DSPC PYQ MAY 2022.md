![[Pasted image 20231024001213.png]]
1. **Scalability**:
   - One of the primary benefits of distributed systems is their ability to scale easily. As workloads and demands increase, additional machines or resources can be added to the system without significant disruption. This horizontal scalability allows distributed systems to handle growing user bases or data loads effectively.

2. **Fault Tolerance**:
   - Distributed systems are designed to be fault-tolerant. They can continue to function even in the presence of hardware failures, network issues, or other types of failures. Redundancy and replication techniques are commonly used to ensure high availability and reliability.

3. **Improved Performance**:
   - Distributed systems can provide better performance by distributing tasks and data across multiple machines. Load balancing mechanisms can evenly distribute workloads, preventing any single machine from becoming a bottleneck. This leads to faster response times and improved resource utilization.

4. **Geographic Distribution and Accessibility**:
   - Distributed systems allow data and services to be accessible from multiple geographical locations. This is essential for applications that require global reach, such as content delivery networks (CDNs) or cloud computing services. Geographic distribution also enhances disaster recovery and data availability.

![[Pasted image 20231024001355.png]]
1. **Scalability**:
   - In a social network, the user base can grow significantly over time. Distributed systems allow these platforms to handle the increasing number of users, posts, and interactions. By adding more servers and resources as needed, the social network can ensure that the platform remains responsive even as the user base expands.

2. **Fault Tolerance**:
   - Social networks are expected to be available 24/7. Distributed systems use redundancy and replication to ensure fault tolerance. Data is often replicated across multiple data centers or servers to prevent service interruptions in case of hardware failures or network issues. Users can access their accounts and content without disruption.

3. **Improved Performance**:
   - Social networks generate and serve a vast amount of content, including text, images, and videos. Distributed systems use load balancing to evenly distribute user requests and content delivery. This prevents any single server from becoming overwhelmed, leading to faster response times and a smoother user experience, even during peak usage.

4. **Geographic Distribution and Accessibility**:
   - Social networks aim to be globally accessible. Distributed systems allow these networks to host data and services in multiple data centers or regions around the world. This geographic distribution reduces latency for users in different locations and ensures content is available even if one data center experiences issues. It also enhances content delivery through content delivery networks (CDNs).


![[Pasted image 20231024001605.png]]

1. **Single Point of Failure**: It relies on a central time server, making the system vulnerable to failures of this server.

2. **Network Latency**: It assumes constant and symmetric network latency, which may not hold true in real-world distributed networks, leading to synchronization inaccuracies.

3. **Security Concerns**: The algorithm lacks security and authentication mechanisms, making it susceptible to attacks like time spoofing.

![[Pasted image 20231024002431.png]]
Process migration in a distributed system is the act of moving a running process from one node (machine) to another within the same distributed environment. This operation is performed for various reasons, including:

1. **Load Balancing**:
   - Load balancing is one of the primary reasons for process migration. It aims to distribute the computational load evenly across all nodes in the distributed system. When some nodes become heavily loaded, processes are migrated to underutilized nodes to maintain efficient resource utilization.

2. **Resource Utilization**:
   - To optimize resource utilization, processes may be migrated to nodes with available resources, such as CPU, memory, or specialized hardware accelerators. This ensures that processes run with maximum efficiency and without resource shortages.

3. **Fault Tolerance**:
   - Process migration can enhance fault tolerance. If a node experiences hardware or software failures, processes running on that node can be migrated to healthy nodes to ensure continued operation. This contributes to the system's reliability.

4. **Energy Efficiency**:
   - In energy-aware distributed systems, process migration can be used to consolidate processes on a subset of nodes and power down unused nodes. This reduces energy consumption and helps lower operational costs, especially in data centers or cloud environments.

These reasons reflect the importance of process migration as a resource management strategy to optimize performance, reliability, and efficiency in distributed systems.

![[Pasted image 20231024002729.png]]

| Aspect               | Load Sharing                            | Load Balancing                           |
|----------------------|----------------------------------------|-----------------------------------------|
| **Definition**      | Multiple systems work independently on different portions of a task. | Tasks are evenly distributed to optimize resource utilization. |
| **Coordination**    | No centralized coordination or control.  | Centralized coordination and control (load balancer). |
| **Suitable For**    | Situations with uneven workloads.       | Evenly distributed workloads.           |
| **Example**         | Multiple file servers independently serving different files. | Load balancing web requests across multiple servers in a farm. |
| **Preferred When**  | Uneven workloads and workload predictability are essential. | Evenly distributing workloads and optimizing resource usage are critical. |

In summary, Load Sharing involves independent work distribution, whereas Load Balancing focuses on coordinated, even workload distribution to optimize resource utilization. Load Balancing is preferred when workloads can be evenly distributed, and resource usage needs optimization.

![[Pasted image 20231024002852.png]]

Certainly, here's the information presented in a table and with concise descriptions:

| Aspect                      | Producer Process                             | Consumer Process                            |
|-----------------------------|--------------------------------------------|---------------------------------------------|
| **Shared Resource**        | Shared buffer or queue where data items are placed. | Shared buffer or queue from which data items are retrieved. |
| **Multiple Entities**      | Multiple producer threads or processes add data. | Multiple consumer threads or processes retrieve data. |
| **Concurrency**             | Simultaneous attempts by producer entities to add data. | Simultaneous attempts by consumer entities to retrieve data. |
| **Lack of Synchronization** | Lack of synchronization mechanisms (locks, semaphores) leads to race conditions. | Lack of proper synchronization results in race conditions. |
| **Consequences**           | Overwriting data, data loss, and inconsistent states in the shared buffer. | Data duplication, data loss, or inconsistency due to concurrent access. |

In summary, race conditions in both the producer and consumer processes occur when multiple threads or processes contend to access shared resources without proper synchronization, leading to data corruption and inconsistencies. Synchronization mechanisms are needed to prevent such issues.

![[Pasted image 20231024002918.png]]

Mutual Exclusion, using locks and mutex where it ensures that only 1 thread can access the critical section, once it is done it would release the mutex so that other thread can access to the critical section. This can prevent race condition

![[Pasted image 20231024003109.png]]

Bernstein's conditions are used to evaluate whether it's safe to parallelize a loop, allowing multiple processors to work on different parts of the loop concurrently. These conditions ensure that there are no data dependencies that could lead to incorrect results. Three conditions are considered:

1. Loop Iterations Independence: Ensure that loop iterations don't write to the same memory locations simultaneously, preventing write-after-write or write-after-read dependencies.

2. Loop Iterations Ordering: Confirm that the order of execution doesn't affect the results, avoiding read-after-write dependencies.

3. Loop Iterations Iteration Space Partitioning: Verify that loop iterations can be divided into distinct partitions, allowing for parallel execution without conflicts.

If Bernstein's conditions are met, it's safe to parallelize the loop. If not, caution and synchronization mechanisms may be needed to ensure correctness in parallel execution.

![[Pasted image 20231024003346.png]]

| Data Dependency Type | Description                                    | Example Code Statements                               |
|----------------------|----------------------------------------------|--------------------------------------------------------|
| Read-After-Write (RAW) | Occurs when a read operation depends on a previous write operation. The read uses a value produced by a write. | ```a = 5; b = a * 2;``` |
| Write-After-Read (WAR) | Occurs when a write operation depends on a previous read operation. The write overwrites a value read by another operation. | ```b = a * 2; a = 5;``` |
| Write-After-Write (WAW) | Occurs when a write operation depends on a previous write operation. Both writes modify the same data, and the order of execution matters. | ```a = 5; a = a * 2;``` |

![[Pasted image 20231024003529.png]]


To analyze the dependencies among the three instructions (h, I2, h) using Bernstein's conditions, let's consider each type of dependency (RAW, WAR, and WAW) separately:

1. **Read-After-Write (RAW)**:
   - RAW dependency occurs when an instruction reads a value produced by a previous instruction.
   - In this case, there is a RAW dependency between instruction I2 and the first occurrence of "h" because I2 reads the result of the computation within "h" (i.e., `(a + b) / (a * b)`).

2. **Write-After-Read (WAR)**:
   - WAR dependency occurs when an instruction overwrites a value that is read by a later instruction.
   - In this case, there is a WAR dependency between the first occurrence of "h" and the second occurrence of "h" because the first "h" computes a value that is later overwritten by the second "h."

3. **Write-After-Write (WAW)**:
   - WAW dependency occurs when two instructions write to the same location, and the order of execution affects the final result.
   - In this case, there is a WAW dependency between the first occurrence of "h" and the second occurrence of "h" because both instructions write to the same variable "x." The order of execution could affect the final value of "x."

In summary, there are dependencies among the three instructions as follows:

- RAW dependency between I2 and the first "h."
- WAR dependency between the first "h" and the second "h."
- WAW dependency between the first "h" and the second "h."
![[Pasted image 20231024003712.png]]
Amdahl's Law is used to predict the overall system speedup when a portion of a program is improved or enhanced to run at a certain speedup factor. Amdahl's Law is given by the formula:

$$S = \frac{1}{(1-P) + \frac{P}{E}}$$

Where:
- \(S\) is the overall system speedup.
- \(P\) is the fraction of the program that can be enhanced or parallelized.
- \(E\) is the speedup factor achieved by the enhanced portion of the program.

Now, let's apply Amdahl's Law to the given scenarios:

(i) **20 percent of the code enhanced to run 1.2 times faster**:

- \(P = 0.20\) (20 percent of the code can be enhanced).
- \(E = 1.2\) (the enhanced portion runs 1.2 times faster).

Using Amdahl's Law:

$$S = \frac{1}{(1-0.20) + \frac{0.20}{1.2}} = \frac{1}{{0.80 + 0.1667}} \approx \frac{1}{0.9667} \approx 1.0344$$

So, the overall system speedup is approximately 1.0344 times.

(ii) **40 percent of the code enhanced**:

- \(P = 0.40\) (40 percent of the code can be enhanced).

Now, we want to find the speedup factor (\(E\)) required to make the system go 2 times faster (\(S = 2\)).

Using Amdahl's Law:

$$2 = \frac{1}{(1-0.40) + \frac{0.40}{E}}$$

Solving for \(E\):

$$\frac{1}{1-0.40 + \frac{0.40}{E}} = 2$$

$$1-0.40 + \frac{0.40}{E} = \frac{1}{2}$$

$$0.60 + \frac{0.40}{E} = \frac{1}{2}$$

$$\frac{0.40}{E} = \frac{1}{2} - 0.60$$

$$\frac{0.40}{E} = -0.10$$

Now, find \(E\):

$$E = \frac{0.40}{-0.10} = \frac{4}{1} = 4$$


So, to make the system go 2 times faster, you would need an enhancement factor of \(E = 4\) (or a 4x speedup) for the 40 percent of the code that is enhanced.

![[Pasted image 20231024003819.png]]

The time complexity of the parallel search algorithm depends on the type of PRAM (Parallel Random Access Memory) model used. Here, we'll determine the time complexity for each step of the algorithm using EREW (Exclusive Read Exclusive Write), CREW (Concurrent Read Exclusive Write), and CRCW (Concurrent Read Concurrent Write) PRAM models. 

(i) **EREW (Exclusive Read Exclusive Write):**

- Step 1: Inform everyone what x is. This step is straightforward and takes O(1) time, as it's a shared read operation.
- Step 2: Every processor checks N/P numbers and sets a flag. Each processor examines a portion of the data, so in parallel, this step takes O(N/P) time.
- Step 3: Check if any flag is set to 1. This step takes O(1) time as it's another shared read operation.

The overall time complexity in the EREW PRAM model is O(N/P).

(ii) **CREW (Concurrent Read Exclusive Write):**

- Step 1: Inform everyone what x is. Like in EREW, this step takes O(1) time as it's a shared read operation.
- Step 2: Every processor checks N/P numbers and sets a flag. Each processor examines a portion of the data in parallel, taking O(N/P) time.
- Step 3: Check if any flag is set to 1. This step, like Step 1, also takes O(1) time.

The overall time complexity in the CREW PRAM model is O(N/P).

(iii) **CRCW (Concurrent Read Concurrent Write):**

- Step 1: Inform everyone what x is. This step takes O(1) time.
- Step 2: Every processor checks N/P numbers and sets a flag. This step takes O(N/P) time, and multiple processors can write to the same location concurrently.
- Step 3: Check if any flag is set to 1. In the CRCW PRAM, this operation also takes O(1) time, and multiple processors can read concurrently.

The overall time complexity in the CRCW PRAM model is O(N/P).

(iv) **Weakness of PRAM:**

The primary weakness of the PRAM model is that it represents an idealized, theoretical model of parallel computation that may not be efficiently implementable on real parallel architectures. In practice, it's often challenging to design hardware that supports the simultaneous read and write operations described in the CRCW model without encountering issues related to contention and synchronization. Real parallel systems typically involve additional complexities and overhead, such as memory access conflicts, contention resolution, and synchronization mechanisms, making it difficult to achieve the theoretical efficiency of the PRAM model in practice.