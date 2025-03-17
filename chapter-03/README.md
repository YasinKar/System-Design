# Chapter 03 - Storage & databases

## What is ACID in Databases?
ACID is a set of properties that ensure reliable transactions in a database. It stands for:
1. A - Atomicity
2. C - Consistency
3. I - Isolation
4. D - Durability

These properties are critical for relational databases (SQL) to maintain data integrity, especially in applications like banking, finance, and e-commerce.

#### **1. Atomicity (All or Nothing)**
Ensures that a transaction is either fully completed or fully rolled back if something goes wrong.

Example: Transferring money between bank accounts
- Step 1: Deduct $500 from Account A
- Step 2: Add $500 to Account B
- If Step 2 fails, Step 1 is rolled back, ensuring no partial updates.

No incomplete transactions—either everything happens or nothing happens.

#### **2. Consistency (Valid State)**
Ensures that the database remains in a valid state before and after a transaction by enforcing rules and constraints.

Example: A bank transaction should never create negative balances if a rule prevents overdrafts.
If a withdrawal request would cause a negative balance, the transaction fails.

The database follows integrity rules and never ends up in an invalid state.

#### **3. Isolation (Transactions Don’t Interfere)**
Ensures that multiple transactions can occur simultaneously without affecting each other.

Example: Two customers buying the last ticket at the same time
- Transaction 1: Checks available tickets (1 left)
- Transaction 2: Also checks available tickets (1 left)
Without Isolation, both could buy the last ticket, causing overbooking.

Transactions are processed independently and in isolation, preventing data corruption.

#### **4. Durability (Data is Permanently Saved)**
Ensures that once a transaction is committed, it remains stored—even in case of power failure or crash.

Example: A completed bank transfer should remain saved, even if the server crashes after confirmation.
Data remains safe after a successful transaction, even in case of system failure.

## SQL vs. NoSQL
When designing a system, choosing between SQL (relational databases) and NoSQL (non-relational databases) depends on factors like scalability, flexibility, and consistency. Below is a comparison of both in terms of advantages and disadvantages in system design.

### SQL (Relational Databases)
SQL databases store data in structured tables with fixed schemas and use SQL (Structured Query Language) for querying.

#### **Advantages**
- ACID Compliance – Ensures Atomicity, Consistency, Isolation, and Durability, making SQL databases ideal for systems requiring data integrity (e.g., banking, financial transactions).
- Structured Data – Best suited for applications with clearly defined relationships between entities (e.g., a CRM system managing customers and orders).
- Powerful Querying – SQL provides advanced querying capabilities, including JOINs, transactions, and complex aggregations.
- Standardized Language – SQL is widely adopted, making it easier to find developers and integrate with various tools.

#### **Disadvantages**
- Scalability Issues – Scaling SQL databases horizontally (sharding) is complex; they are primarily designed for vertical scaling (adding more power to a single server).
- Fixed Schema – Changing the database schema requires migrations, which can be time-consuming and risky for rapidly evolving applications.
- Performance Bottlenecks – High-traffic applications with many read/write operations may suffer from performance degradation due to strict consistency enforcement.

#### **Use Cases**
- Banking & Finance (due to ACID compliance)
- ERP and CRM Systems
- Traditional Web Applications

#### **Common SQL Databases**
**1. MySQL**
- Open-source and widely used
- Supports replication and clustering
- Strong ACID compliance with InnoDB engine
- Best for: Web applications, e-commerce, banking

**2. PostgreSQL**
- Advanced open-source database
- Supports JSON data along with relational tables
- High concurrency with MVCC (Multi-Version Concurrency Control)
- Best for: Data analytics, geospatial applications, enterprise apps

3. **Microsoft SQL Server**
- Developed by Microsoft
- Supports high availability and business intelligence tools
- Strong security with encryption and role-based access
- Best for: Enterprise solutions, Windows-based applications

4. **Oracle Database**
- High-performance enterprise-grade database
- Supports partitioning, sharding, and strong security
- Ideal for large-scale applications with complex transactions
- Best for: Banking, large-scale enterprise applications

5. **SQLite**
- Lightweight, serverless database
- Used for mobile and embedded applications
- No need for a separate server process
- Best for: Mobile apps, IoT devices, small-scale apps

### NoSQL (Non-Relational Databases)
NoSQL databases are schema-less and can store data in different formats: key-value, document, column-family, and graph databases.

#### **Advantages**
- Scalability – Designed for horizontal scaling (adding more servers), making them ideal for distributed systems and high-traffic applications.
- Flexible Schema – Schema-less structure allows easy modifications, making NoSQL databases suitable for dynamic applications.
- High Performance – Optimized for fast reads and writes, especially in distributed environments (e.g., caching layers).
- Best for Unstructured Data – Can handle large volumes of JSON, XML, and semi-structured data, making them great for applications like real-time analytics, social media, and IoT.

#### **Disadvantages**
- Lack of ACID Compliance – Most NoSQL databases follow BASE (Basically Available, Soft state, Eventually consistent), which may result in data inconsistency.
- Limited Querying Capabilities – NoSQL databases lack JOINs and complex queries like SQL, requiring additional processing logic in the application.
- Data Redundancy – Since there are no relationships like in SQL, duplicate data is often stored, leading to data inconsistency.
- Less Mature Ecosystem – NoSQL tools and expertise are not as widespread as SQL, which can make development more challenging.

#### **Use Cases**
- Real-time analytics and Big Data
- IoT and streaming applications
- Social media and recommendation systems
- Content management systems (CMS)

#### **Common SQL Databases**

**1. MongoDB (Document-based)**
- Stores data in JSON-like BSON format
- Supports flexible schema and indexing
- Scales horizontally using sharding
- Best for: CMS, real-time analytics, IoT

**2. Cassandra (Column-family)**
- Distributed, highly scalable database
- Designed for high availability (No single point of failure)
- Used by companies like Facebook, Netflix
- Best for: Big data, real-time analytics

**3. Redis (Key-Value Store)**
- In-memory database for ultra-fast performance
- Supports caching, pub/sub messaging, and session storage
- Best for: Caching, gaming leaderboards, real-time data processing

**4. Firebase Firestore (Document-based)**
- NoSQL database managed by Google
- Real-time syncing for mobile and web apps
- Best for: Mobile apps, real-time chat applications

**5. Neo4j (Graph-based)**
- Optimized for graph-based relationships
- Uses Cypher Query Language (CQL)
- Best for: Social networks, recommendation systems, fraud detection
  
### SQL vs. NoSQL
| **Criteria**          | **SQL (Relational)**            | **NoSQL (Non-Relational)**      |
|----------------------|--------------------------------|--------------------------------|
| **Data Structure**   | Structured with fixed schema  | Unstructured or semi-structured |
| **Scalability**      | Vertical (Single Server)      | Horizontal (Multiple Servers)  |
| **ACID Compliance**  | Strong (for data integrity)   | Weak (Eventual consistency)    |
| **Performance**      | Slower for large datasets     | Faster for read-heavy workloads |
| **Use Case**        | Banking, ERP, CRM, E-commerce | Big Data, Social Media, IoT, Caching |
