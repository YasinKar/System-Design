# System Design

## What is __System Design__?
System design is the process of designing the architecture of a software system, which involves making decisions about its structure, components, connections, data, and how it will scale. The goal of system design is to build a stable, scalable, accessible, and efficient system that can meet the needs of users well.

## Why System Design is Important?
Imagine you are a software engineer tasked with designing a system for managing 10 million players, grouping them into teams of 10 based on their skill level. Given that an average of 10,000 players are online at any given time, querying the database each time a player comes online or goes offline to change it status would be inefficient. Additionally, real-time changes in player status could lead to inaccuracies in matchmaking.

### Optimized Approach
To ensure both speed and accuracy, we can implement a **queue-based matchmaking system** using an **in-memory database like Redis**. Here’s how it works:

- Players are placed into **skill-based queues** stored in Redis when they start matchmaking.
- A **matchmaking service** continuously pulls players from these queues to form teams of 10.
- If a queue lacks enough players, a **timeout mechanism** expands the skill range slightly to allow near-skill-level players to be grouped together.
- **Redis Pub/Sub or WebSockets** can be used to track real-time player status changes, reducing database load and improving accuracy.

### Comparison Table

| Feature                   | Direct Database Querying | Queue-Based Matching with Redis |
|---------------------------|-------------------------|--------------------------------|
| **Performance**          | Slow, due to frequent DB queries | Fast, as Redis operates in-memory |
| **Accuracy**             | Can lose accuracy due to real-time status changes | More accurate with Pub/Sub updates |
| **Scalability**          | Limited, as database queries increase with players | Highly scalable with distributed Redis instances |
| **Latency**              | High, as database operations take time | Low, as Redis fetches data in milliseconds |
| **Flexibility**          | Hard to adjust matchmaking criteria dynamically | Supports dynamic skill-range adjustments with timeouts |
| **Resource Usage**       | High database load | Efficient memory usage with minimal DB writes |

By leveraging Redis, we improve matchmaking efficiency while reducing strain on the database. This ensures a fast, scalable, and accurate player grouping system.

<br>

- [Chapter 01 - Basics Of Distributed Systems](https://github.com/YasinKar/System-Design/tree/main/chapter-01)
  - [What is Distributed Systems?](https://github.com/YasinKar/System-Design/tree/main/chapter-01#what-is-distributed-systems)
  - [CAP Theorem (Consistency, Availability, Partition Tolerance)](https://github.com/YasinKar/System-Design/tree/main/chapter-01#cap-theorem-consistency-availability-partition-tolerance)
  - [Consistency Models (Strong, Eventual, Weak Consistency)](https://github.com/YasinKar/System-Design/tree/main/chapter-01#consistency-models-strong-eventual-weak-consistency)
  - [Scalability (Vertical vs. Horizontal Scaling)](https://github.com/YasinKar/System-Design/tree/main/chapter-01#scalability-vertical-vs-horizontal-scaling)
  - [On-Demand Virtualization Automation](https://github.com/YasinKar/System-Design/tree/main/chapter-01#on-demand-virtualization-automation)
  - [Load Balancing](https://github.com/YasinKar/System-Design/tree/main/chapter-01#load-balancing)
  - [Data Replication & Sharding](https://github.com/YasinKar/System-Design/tree/main/chapter-01#data-replication--sharding)

- [Chapter 02 - Networking](https://github.com/YasinKar/System-Design/tree/main/chapter-02)
  - [Client-Server Communication & Network Protocols](https://github.com/YasinKar/System-Design/tree/main/chapter-02#client-server-communication--network-protocols)
  - [Routing & Proxies in Networking](https://github.com/YasinKar/System-Design/tree/main/chapter-02#routing--proxies-in-networking)
  - [Content Delivery Network (CDN) & Edge Networking](https://github.com/YasinKar/System-Design/tree/main/chapter-02#content-delivery-network-cdn--edge-networking)

- [Chapter 03 - Storage & Databases](https://github.com/YasinKar/System-Design/tree/main/chapter-03)
  - [What is ACID in Databases?](https://github.com/YasinKar/System-Design/tree/main/chapter-03#what-is-acid-in-databases)
  - [SQL vs. NoSQL](https://github.com/YasinKar/System-Design/tree/main/chapter-03#sql-vs-nosql)

- [Chapter 04 - Caching](https://github.com/YasinKar/System-Design/tree/main/chapter-04)
    - [What is Caching?](https://github.com/YasinKar/System-Design/tree/main/chapter-04#what-is-caching)
    - [Types of Cache](https://github.com/YasinKar/System-Design/tree/main/chapter-04#types-of-cache)
    - [Cache Invalidation Strategies](https://github.com/YasinKar/System-Design/tree/main/chapter-04#cache-invalidation-strategies)

- [Chapter 05 - Message Queues & Event-Driven Architecture](https://github.com/YasinKar/System-Design/tree/main/chapter-05)
    - [Event-Driven Architecture (EDA)](https://github.com/YasinKar/System-Design/tree/main/chapter-05#event-driven-architecture-eda)
    - [Message Queues](https://github.com/YasinKar/System-Design/tree/main/chapter-05#message-queues)

- [Chapter 06 - API Design](https://github.com/YasinKar/System-Design/tree/main/chapter-06)
    - [API Design and Its Types](https://github.com/YasinKar/System-Design/tree/main/chapter-06#api-design-and-its-types)
    - [Rate Limiting & Throttling](https://github.com/YasinKar/System-Design/tree/main/chapter-06#rate-limiting--throttling)
    - [Service Mesh & API Gateway](https://github.com/YasinKar/System-Design/tree/main/chapter-06#service-mesh--api-gateway)

- [Chapter 07 - System Security](https://github.com/YasinKar/System-Design/tree/main/chapter-07)
    - [Authentication & Authorization](https://github.com/YasinKar/System-Design/tree/main/chapter-07#authentication--authorization)
    - [Encryption](https://github.com/YasinKar/System-Design/tree/main/chapter-07#encryption)
    - [Common Vulnerabilities](https://github.com/YasinKar/System-Design/tree/main/chapter-07#common-vulnerabilities)

- [Chapter 08 - Monitoring & Logging and Error Management](https://github.com/YasinKar/System-Design/tree/main/chapter-08)
    - [Observability](https://github.com/YasinKar/System-Design/tree/main/chapter-08#observability)
    - [Encryption](https://github.com/YasinKar/System-Design/tree/main/chapter-08#monitoring-tools)
    - [Fault Tolerance & Circuit Breaker Pattern](https://github.com/YasinKar/System-Design/tree/main/chapter-08#fault-tolerance--circuit-breaker-pattern)


<br><br> ***author*** : [Yasin Karbasi](https://github.com/YasinKar)
