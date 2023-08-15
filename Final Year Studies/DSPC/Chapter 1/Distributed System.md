## Meaning
> A computing environment in which various components are spread across multiple computers

keywords : **various components**, **spread  across multiple computers**

## Purpose of this concept
We break big computation into multiple processing entities

> Imagine you have a task to count 0 - 10000, try to think whether you count alone from 0 - 1000 is faster or splitting into multiple people to count at the same time is faster

## What can be distributed
- Database/data
- Operating System
- File System
- Business Logic
- Authentication
- Workload (Resources allocation/ load sharing)

## What are the benefits?

### Scalability
Distributed System are made up of **multiple nodes**, therefore when trying to scale the system up, we have 2 approach 

**Horizontal Scalability** -> Add more nodes and pcs into the system (Add more server)
**Vertical Scalability** -> We upgrade the existing nodes to better node (Upgrade Server Specs)

### Reliability
Distributed system can **keep delivering** its services even when one or several of its **software/hardware component fails**

Let say you have a Database Server hosted for your FYP,
just in case of the system fails, you have a **replica database** that copies the data from the main database. So let say if your main database fails, you can still use your **replica database** to continue deliver data

### Performance

Referring to main concept, distributed system is about **distributing the workload** across multiple nodes, each node can handle a smaller amount of work, which improve overall performance of the system. 

Distributed System can use [[parallel processing]] , which improve performance

A web server can be distributed across multiple nodes to handle more request, so like each node handle like 30%, so with 3 nodes, then we split the workload when handling huge amount of request, therefore it improve the performance

### Geographically

Each of the nodes inside the distributed system can be put physically based on the decision of the location that we like, we have the freedom to choose where we can put each of the node when building a distributed system

This helps to improve security since when performing attack to physical device, the attacker need to go to multiple location

## Challenges of Building One

### Avoid single point of failure

Single Point of Failure means that when a single component inside the distributed system fails, the entire system down

When dealing with SPOF, it is not easy to determine which of the component is the SPOF of the system

It is hard to design a system that does not have SPOF component

### Replication 

Replication means that we make copy of some of the components of the distributed system, for example like the component that is identified as SPOF.

So imagine if SPOF really fails, then the replication can replace it to ensure reliability.

But the actual issue of replication is when make a new replication we have to consider these elements
- Data consistency -> its not easy to maintain data consistency from the main node and the replica node
- Latency -> Since the components are spread among the system, therefore for the communication when sending the data would confirm have some delay
- Bandwidth -> Replication consume bandwidth, because you constantly making the data replicated to multiple nodes
- Cost -> Replication means copy and add more -> buy software/hardware -> pay money -> cost high

### Availability & Performance

It is not easy to ensure each of the nodes would not fail
It is not easy to ensure each capacity of the nodes can handle huge amount of workload

### Resource naming, addressing and location of resources.

Its hard to manage to resources since it is distributed among the system

It is not easy to access the name, when it is already difficult to find the location of the resources

### Binding

associating a name or address with a resource in a distributed system is not easy as distributed system enlarge

The larger the distributed system, the more complex the binding is as  the system would consist of even more resources










