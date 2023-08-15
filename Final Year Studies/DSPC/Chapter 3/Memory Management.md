## Jargons to note
#### Section 1
- Virtual Memory
#### Section 2
- Simple Memory Model
- Shared Memory Model
- Bus Contention
- Shared Memory Performance
- OpenMP****
- Distributed Shared Memory (DSM)
- DSM Management
- Distributing Shared Data
- DSM Performance
- Distributed Memory Programming (MPI)
- MPI (Message Passing Interface)
	- Why?
	- basic functions
- Frameworks (MPI, FORK, pthread_create, OpenMP) (Comparison)
- Synchronous Sending and Receiving
- Asynchronous Sending and Receiving
- MPI Send / Receive Operation
#### Section 3
- Memory Migration
	- Vector Add Example


## Virtual Memory
- Its a memory management technique that allows a computer to use more memory than is physically available.
- Memory can be divided into two parts
	- Virtual Memory -> Logical Memory seen by the user, memory that the user thinks they have
	- Physical Memory -> Actual Memory that is available inside the computer that the computer can use
- Virtual Memory works by mapping virtual memory address to physical address

![[Drawing 2023-07-31 13.50.45.excalidraw]]

## Simple Memory Model ***
- access time for all processors are equal
- requires strict control of degree of multi-programming
- often does not use virtual memory or caching because of overhead

## Shared Memory Model ***

### Concept
> A method of inter-process communication (IPC) in which multiple processes can access the same memory space

- Usually used in multiprocessing systems, where multiple processors share the same physical memory (RAMS, Local Cache, Secondary Storage)
- Potential Issues when using this model can be **bus contention**

### Example
- OpenMP Framework (C++ shit)

## Bus Contention

### Concept
> a situation in computer design where two or more devices on a bus attempt to place values on it at the same time.  This can cause problems because the bus can only carry one value at a time.

### Example

Two devices, A and B are connected to a bus. Device A wants to write a value of 1 to the bus, and device B wants to write a value of 0 to the bus. If both devices try to write to the bus at the same time, the bus will not be able to determine which value to write, and the result will be unpredictable.

![[Drawing 2023-07-31 14.03.08.excalidraw]]

### Ways to Avoid

- use bus arbiter, bus aribiter allocate limited time for each of the device to access the bus at any given time. It has the list of priorities for each device to access the bus, therefore with priority and time, the bus arbiter can decide which can interrupt or which cannot be access at the current based on the priority

### Effect of Bus Contention

- Data corruption -> 2 device change data at the same time then data corrupt
- Performance degradation -> The bus cannot decide which device can access to the bus therefore it reduce the performance 
- System crashed -> in more extreme cases, the system can be crashed\

## Shared Memory Performance

### Why shared memory would improve the performance?
- Allowing processes to access data without having to copy it between different memory space (because its shared)

### Factors that affect the performance
- **the size of the shared memory space**, the more data can be shared, higher the performance
- **number of processes that are accessing the shared memory space**, the more processes that access the shared memory space, the chance of having **contention** is higher, which can decrease performance
- **type of data that is being shared**, int and floats is easier to shared compared strings and objects
- **the operating system**, operating system works for managing the shared memory, some os is better at managing the shared memory

## Threading

### Jargons
- Threads -> lightweight process that can run concurrently with other threads in a single process, they share same address space and resources, but each of them have their own stack and registers. 

### What for ?
- Allow multiple tasks to run simultaneously
- Allow task to be executed in parallel
- allowing tasks to be scheduld more efficiently

### Problem will be faced by threads
- Race Condition -> two or more threads accessing same data at same time
- Deadlocks -> When threads are waiting each other to release a resource
- Synchronization -> syncing data with each other

## OpenMP

> API that we use for doing multithreading

### Sample code using pragma in C++

```c++

#pragma omp parallel for
for (int i = 0; i < n; i++){

	//This is the parallel region of the codebase	

}
```

## Distributed Shared Memory

### Concept
> Memory management technique that allows multiple processes to access the same memory space, even if they are running on different computers.








