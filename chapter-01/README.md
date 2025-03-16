# Basics of distributed systems

## What Is Distributed Systems?
in distributed systems, software is divided into independent and scalable components. These components and services collaborate to function as an integrated system. Typically, they are networked and communicate with each other to provide a unified service

### Features of distributed systems
- **Transparency** – Users should not be aware that the system consists of multiple nodes. Transparency applies to access, location, migration, concurrency, and failure handling.

- **Scalability** – The system should efficiently accommodate an increasing number of nodes without performance degradation.

- **Fault Tolerance** – The system must continue functioning even if some nodes fail, ensuring high availability and reliability.

- **Concurrency** – Multiple processes or users should be able to interact with the system simultaneously without conflicts.

- **Coordination** – Nodes must synchronize and manage data and processing efficiently to maintain system integrity.

- **Security** – Authentication, authorization, and data protection mechanisms must be in place to prevent attacks and ensure secure communication.

### Common Architectures in Distributed Systems

- **Client-Server Architecture** – Clients send requests to a central server, which processes them and returns responses.

- **Peer-to-Peer (P2P) Architecture** – Each node acts as both a client and a server, sharing resources directly without a central authority.

- **Microservices Architecture** – The system is divided into independent services, each handling a specific function, communicating via APIs.

- **Event-Driven Architecture** – Components communicate asynchronously by sending and responding to events rather than direct calls.

- **Service-Oriented Architecture (SOA)** – Services interact over a network using standardized protocols, promoting reusability and interoperability.

- **Serverless Architecture** – Applications are executed in a cloud-based environment where resources are allocated dynamically, reducing infrastructure management overhead.

### Monolithic vs. Distributed Systems Comparison

| Aspect                | Monolithic System | Distributed System |
|----------------------|------------------|-------------------|
| **Architecture**    | Single, unified application | Multiple independent services |
| **Scalability**     | Limited; scaling requires duplicating the whole system | High; can scale individual components separately |
| **Deployment**      | Easier, as everything is in one place | More complex, requiring orchestration tools (e.g., Kubernetes) |
| **Development Speed** | Faster for small projects | Slower due to complexity and inter-service communication |
| **Maintenance**     | Can become difficult as the codebase grows | Easier to maintain individual components |
| **Fault Tolerance** | A failure in one part may crash the entire system | More resilient, failures in one service don’t affect others (if properly designed) |
| **Performance**     | Can be efficient for small applications | Better suited for large-scale applications with high traffic |
| **Flexibility**     | Less flexible; changing one part affects the whole system | More flexible; services can be modified independently |
| **Technology Stack** | Typically uses a single technology stack | Allows different services to use different technologies |
| **Security**        | Easier to secure since everything is in one place | More complex security due to multiple entry points |
| **Cost**           | Lower initial cost but higher long-term maintenance cost | Higher initial investment but more cost-effective at scale |
| **Time to Market**  | Faster for simple applications | Slower due to the need for managing multiple components |
| **Examples**       | Traditional enterprise applications, CMS, ERP | Cloud-native applications, e-commerce, microservices-based platforms |

## CAP Theorem (Consistency, Availability, Partition Tolerance)
The CAP Theorem, introduced by Eric Brewer, states that in a distributed system, it is impossible to guarantee all three of the following properties simultaneously. A system can only achieve two out of the three:

- **Consistency (C)** – Every node sees the same data at the same time. When an update occurs, all subsequent reads will return the latest data.

- **Availability (A)** – The system always responds to requests, even if some nodes fail or some data is outdated.

- **Partition Tolerance (P)** – The system can continue operating even if network failures cause some nodes to become unreachable.

### Key Considerations in CAP Theorem
- **Trade-off in distributed systems** – You must choose between Consistency, Availability, and Partition Tolerance, as achieving all three simultaneously is impossible.

- **System classifications based on CAP**
    - **CP (Consistency + Partition Tolerance)** – Ensures data consistency but may reject some requests during network failures. (e.g., MongoDB, HBase)
    - **AP (Availability + Partition Tolerance)** – Guarantees responses but may return outdated or inconsistent data. (e.g., Cassandra, DynamoDB)
    - **CA (Consistency + Availability)** – This combination is impossible in distributed systems since network failures (Partitions) are inevitable. However, it is achievable in non-distributed systems like traditional SQL databases (PostgreSQL, SQL Server).

- **Impact on system design**
  - If Consistency is a priority (e.g., banking systems), Availability may be reduced to prevent data inconsistency.
  - If Availability is more important (e.g., social networks), Consistency may be sacrificed temporarily.

- **Real-world implementations**
    - Many NoSQL databases prioritize AP or CP over full consistency.
    - SQL databases typically focus on Consistency rather than Availability.


<br> ![CAP Theorem](https://github.com/YasinKar/System-Design/blob/main/chapter-01/CAP_Theorem.webp)

## Consistency Models (Strong, Eventual, Weak Consistency)
In distributed systems, consistency models define how updates to data are propagated across different nodes and what guarantees the system provides regarding data visibility. The main types of consistency models are:

- **Strong Consistency** – Every read operation always returns the most recent write. Once data is updated, all nodes immediately reflect the latest change.

- **Eventual Consistency** – The system does not guarantee immediate consistency, but all nodes will eventually converge to the same state.

- **Weak Consistency** – There is no guarantee that all nodes will see the latest update, even after some time.

| Consistency Model | Guarantee | Performance | Use Case Example | System Examples |
|----------------------|----------------------|----------------------|----------------------|----------------------|
| **Strong Consistency**    | Always the latest data | High latency | Banking, stock trading | Spanner, SQL (ACID-compliant) |
| **Eventual Consistency**     | Data converges over time | Medium latency | Social media, DNS, CDN | DynamoDB, Cassandra |
| **Weak Consistency**      | No guarantee of up-to-date data | Low latency | Video streaming, gaming | UDP-based systems |

## Scalability (Vertical vs. Horizontal Scaling)
Scalability in system design refers to the ability of a system to handle increased loads or to be expanded to accommodate growth. There are two main types of scalability: Vertical Scaling and Horizontal Scaling. Both have their strengths and weaknesses, and choosing between them depends on factors such as the architecture of the system, the type of load, and cost considerations.

- **Vertical Scaling (Scaling Up)**
Vertical scaling involves adding more power (CPU, RAM, storage) to an existing machine or server. In this approach, you scale by upgrading the existing hardware to handle a larger workload.
Vertical scaling is often used for applications that are difficult to distribute or for workloads where a single machine can handle the task. This includes databases that require a single point of coordination or applications that rely on complex single-threaded operations.

- **Horizontal Scaling (Scaling Out)**
Horizontal scaling involves adding more machines or servers to distribute the load across multiple systems. Instead of upgrading a single server, you increase the number of servers in the system.
This is typically used for systems designed for distributed computing or systems that need to handle large numbers of users concurrently, such as web applications, microservices, or cloud-based systems.

### Comparison of Vertical Scaling vs Horizontal Scaling

| Feature                   | **Vertical Scaling (Scaling Up)**                               | **Horizontal Scaling (Scaling Out)**                          |
|---------------------------|-----------------------------------------------------------------|--------------------------------------------------------------|
| **Definition**             | Adding more resources (CPU, RAM, storage) to an existing server. | Adding more machines or servers to distribute the load.       |
| **Implementation Simplicity** | Easier, typically involves just upgrading hardware.            | More complex, requires designing a distributed architecture.  |
| **Scalability**            | Limited by the physical hardware capacity.                      | Nearly unlimited, can scale by adding more servers.           |
| **Use Case**               | Suitable for applications needing powerful hardware.            | Suitable for large, distributed systems handling high traffic. |
| **Cost**                   | Costs increase as hardware is upgraded.                        | Can be more cost-effective by using cheaper, smaller servers. |
| **Drawback**               | Limited by hardware upgrades.                                  | Complexity in managing data consistency and network latency.  |
| **Fault Tolerance**        | Single point of failure—if the server fails, the system goes down. | Better fault tolerance with distributed systems.              |
| **Database Considerations**| Suitable for centralized databases that require high performance. | Requires data partitioning (sharding) and distributed systems. |
| **Development Simplicity** | Less complex, requires fewer changes to software and architecture. | Requires more complex design and distributed system management. |


## On-Demand Virtualization Automation
On-demand virtualization automation refers to the process of dynamically creating, managing, and terminating virtual machines (VMs) or containers based on real-time demand. This approach optimizes resource utilization, reduces costs, and enhances scalability without manual intervention.
In this approach, we create or delete machines and allocate resources to them on demand using scripts.

### Key Benefits
- **Optimized Resource Utilization**
Automatically allocates computing resources (CPU, RAM, storage) only when needed, preventing wastage.

- **Cost Efficiency**
Reduces operational costs by eliminating the need for over-provisioning.

- **Improved Scalability**
Dynamically scales up or down based on workload demands, ensuring seamless performance.

- **Simplified Infrastructure Management**
Centralized monitoring and automated provisioning simplify administration.

- **Reduced Deployment Time**
Enables faster deployment of applications, VMs, and containers with minimal manual configuration.


## Load Balancing
Load Balancing is a crucial concept in designing scalable and distributed systems. The primary goal of a Load Balancer is to distribute incoming requests across multiple servers or services to ensure better performance, higher availability, and prevent overloading a single server.

### Why Use a Load Balancer?
- **Scalability** – Distributes traffic to multiple servers, increasing system capacity.
- **Fault Tolerance** – If one server fails, the Load Balancer redirects requests to healthy servers.
- **Performance Optimization** – Ensures faster request processing by balancing the workload.
- **Even Load Distribution** – Prevents a single server from being overloaded while others remain underutilized.

### Types of Load Balancing Algorithms

1. **Round Robin** –
Requests are distributed sequentially across available servers. For example, with three servers A, B, and C:
Request 1 → A
Request 2 → B
Request 3 → C
Request 4 → A ...

- Pros
    - Simple and effective for homogeneous servers.
- Cons
    - If a server is slower, it may still receive the same number of requests, causing imbalances.

2. **Weighted Round Robin** –
An improved version of Round Robin where each server is assigned a weight. More powerful servers receive more requests.

- Pros
    - Suitable for environments with servers of different capacities.
- Cons
    - Requires careful weight tuning.

3. **Least Connections** –
Requests are routed to the server with the fewest active connections. This is ideal for stateful applications where request processing time varies.

- Pros
    - Ensures fairer load distribution.
    - Works well for applications with long-running requests.
- Cons
    - May increase latency if the system doesn’t handle connection time efficiently.
 
4. **Least Response Time** –
Requests are sent to the server with the lowest response time, ensuring faster performance.

- Pros
    - Optimized for speed and responsiveness.
- Cons
    - Requires continuous monitoring of response times.
 
5. **IP Hashing** –
Uses a hashing algorithm on the client’s IP address to consistently route a specific client to the same server.

- Pros
    - Useful for session-based applications where users should always connect to the same server.
- Cons
    - If a server fails, redistributing requests can be difficult.
 
6. **Least Bandwidth** –
Routes requests to the server with the least amount of bandwidth usage.

- Pros
    - Ideal for applications that handle large data transfers, such as streaming.
- Cons
    - Requires real-time bandwidth monitoring.

7. **Random** –
Requests are distributed randomly among servers.

- Pros
    - Simple to implement.
- Cons
    - May lead to uneven load distribution.
 
## Data Replication & Sharding
In large-scale distributed systems, Data Replication and Sharding are two essential techniques used to improve performance, scalability, and reliability. While Replication focuses on creating copies of data across multiple nodes for redundancy and availability, Sharding partitions data across multiple nodes to distribute the load efficiently.

### Data Replication
Data Replication is the process of storing copies of the same data on multiple servers or locations to enhance fault tolerance, read scalability, and disaster recovery.

#### Types of Data Replication
1. **Master-Slave Replication (Primary-Replica)** –
A single master node handles all write operations.
One or more slave nodes replicate data from the master and handle read requests.
If the master fails, a slave can be promoted to the new master.

- Pros
    - Improves read performance by distributing queries across multiple replicas.
    - Provides data redundancy.

- Cons
    - Write operations are limited to a single master, which can become a bottleneck.
    - Lag between master and replicas can lead to stale reads.

2. **Master-Master Replication (Active-Active)** –
Multiple nodes act as masters, allowing both read and write operations.
Changes are synchronized across all nodes, either asynchronously or synchronously.

- Pros
    - High availability with no single point of failure.
    - Suitable for geographically distributed applications.
- Cons
    - Handling conflicts when two nodes update the same data simultaneously can be complex.
    - Requires advanced conflict resolution strategies.

3. **Quorum-based Replication (Consensus-driven)** –
Used in distributed databases like Apache Cassandra, Amazon DynamoDB, and Raft-based systems.
Instead of a single master, multiple nodes participate in a consensus algorithm (e.g., Paxos, Raft) to ensure data consistency.

- Pros
    - No single point of failure.
    - Suitable for distributed and decentralized systems.
- Cons
    - Higher latency due to consensus requirements.
 
#### Replication Strategies
**Synchronous Replication** –
Writes are committed to all replicas before acknowledging success.

- Pros – Strong consistency.
- Cons – High latency.

**Asynchronous Replication** –
Writes are acknowledged immediately, and replicas are updated later.

- Pros – Low latency.
- Cons – Risk of data loss in case of failure.

### **Sharding (Data Partitioning)**
Sharding is a technique used to horizontally partition data across multiple database servers to distribute the workload efficiently. Instead of duplicating data, sharding splits it into smaller pieces (shards), each stored on a different node.

#### Sharding Strategies
1. **Hash-based Sharding** –
A hash function is used to distribute records across shards.
Example: shard_id = hash(user_id) % number_of_shards.

- Pros
    - Ensures even distribution of data.
    - Reduces hot-spot issues.
- Cons
    - Resharding (adding more shards) is complex because data must be redistributed.

2. **Range-based Sharding** –
Data is divided based on value ranges.
Example: User IDs 1-1000 → Shard 1, 1001-2000 → Shard 2, etc.

- Pros
    - Simple to implement.
    - Efficient for range queries.
- Cons
    - Uneven distribution can lead to hot-spot problems (e.g., all recent users in one shard).

3. **Directory-based Sharding** –
A lookup table (directory) maps records to specific shards.

- Pros
    - Flexible, as new shards can be added easily.
- Cons
    - The lookup table becomes a single point of failure and performance bottleneck.

4. **Geo-based Sharding** –
Data is partitioned based on geographical location.
Example: Users in Europe → European server, US → US server, etc.

- Pros
    - Reduces latency for users in different regions.
- Cons
    - Some regions may have more load than others, requiring dynamic scaling.
 
| **Feature**      | **Replication** | **Sharding** |
|-----------------|---------------|-------------|
| **Goal**        | Redundancy & availability | Scalability & load distribution |
| **Data Copying** | Full copy on multiple nodes | Split data across multiple nodes |
| **Read Scalability** | High (multiple read replicas) | Depends on query type |
| **Write Scalability** | Limited (single master bottleneck) | High (data is partitioned) |
| **Complexity**  | Easier to implement | Harder to reshard dynamically |
