# Chapter 06 - API Design

## What is API Design
API (Application Programming Interface) design refers to the process of structuring how different software components interact. The goal is to create APIs that are scalable, maintainable, and easy to use. There are several types of API architectures, each serving different use cases.

## Types of APIs

### REST (Representational State Transfer)
- Uses HTTP methods (GET, POST, PUT, DELETE).
- Works with standard formats like JSON and XML.
- Stateless (each request must contain all necessary information).
- Scalable and widely used for web applications.

### GraphQL
- Clients specify the exact data they need.
- Single endpoint (/graphql) handles all requests.
- Reduces over-fetching and under-fetching of data.
- Ideal for complex data relationships and frontend-driven applications.

### gRPC (Google Remote Procedure Call)
- Uses HTTP/2 and Protocol Buffers (protobuf) for efficient data exchange.
- Supports bi-directional streaming.
- Faster and more efficient than REST for high-performance applications.
- Best for microservices and low-latency systems.

### SOAP (Simple Object Access Protocol)
- Uses XML for message format.
- Stronger security and reliability features (e.g., WS-Security).
- Used in enterprise applications (e.g., banking, healthcare).

### WebSockets
- Enables real-time communication with persistent connections.
- Ideal for applications requiring instant data updates (e.g., chat apps, stock market).
- 

| Feature         | REST      | GraphQL   | gRPC       | SOAP       | WebSockets  |
|---------------|----------|-----------|-----------|-----------|------------|
| **Data Format** | JSON, XML | JSON      | Protobuf   | XML       | Custom (Binary/Text) |
| **Communication** | Request/Response | Query-based | Request/Response, Streaming | Request/Response | Full Duplex |
| **Performance** | Medium   | Optimized queries | High (Binary, HTTP/2) | Low (XML overhead) | High |
| **Ease of Use** | High     | Medium    | Low (requires protobuf) | Low | Medium |
| **Use Cases** | Web APIs  | Frontend-heavy apps | Microservices | Enterprise apps | Real-time apps |

## Rate Limiting & Throttling

### Rate Limiting
Rate limiting controls how many requests a client can make within a specific timeframe. It helps prevent abuse and ensures fair resource distribution.

#### **Techniques for Rate Limiting**
- Fixed Window: Limits requests in a fixed time window (e.g., 100 requests per minute).
- Sliding Window: Uses a rolling window to smooth out request distribution.
- Token Bucket: Requests consume tokens from a bucket, which refills at a fixed rate.
- Leaky Bucket: Requests are processed at a fixed rate; excess requests are discarded or queued.

### Throttling
Throttling is the process of slowing down or delaying excessive requests from a client. Unlike rate limiting (which blocks requests outright), throttling allows limited requests at a reduced speed.

| Feature        | Rate Limiting               | Throttling                  |
|---------------|----------------------------|-----------------------------|
| **Purpose**   | Restrict requests          | Slow down requests          |
| **Response**  | Rejects requests when limit exceeds | Allows requests but with delay |
| **Example Use Case** | API quota enforcement | Avoiding server overload |

<br><br> ***author*** : [Yasin Karbasi](https://github.com/YasinKar)
