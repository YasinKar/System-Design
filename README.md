# System Design

## What Is __System Design__?
System design is the process of designing the architecture of a software system, which involves making decisions about its structure, components, connections, data, and how it will scale. The goal of system design is to build a stable, scalable, accessible, and efficient system that can meet the needs of users well.

## Why System Design Is Important?
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


<br> -  [Chapter 01 - Basics of distributed systems](https://github.com/YasinKar/System-Design/tree/main/chapter-01)

<br> -  [Chapter 02 - Networking](https://github.com/YasinKar/System-Design/tree/main/chapter-02)

<br> -  [Chapter 03 - Storage and databases](https://github.com/YasinKar/System-Design/tree/main/chapter-03)

<br> -  [Chapter 04 - Caching](https://github.com/YasinKar/System-Design/tree/main/chapter-04)

<br> -  [Chapter 05 - API design](https://github.com/YasinKar/System-Design/tree/main/chapter-05)

<br> -  [Chapter 06 - System security](https://github.com/YasinKar/System-Design/tree/main/chapter-06)

<br> -  [Chapter 07 - Monitoring & logging and error management](https://github.com/YasinKar/System-Design/tree/main/chapter-07)
