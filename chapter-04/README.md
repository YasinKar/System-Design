# Chapter 04 - Caching

## What is Caching?
Caching is a technique used to store frequently accessed data in a high-speed storage layer to improve performance and reduce load on backend services. Instead of fetching data from a slow source (e.g., database, API, or disk), caching allows retrieval from a fast, temporary storage (e.g., in-memory).

### Why Use Caching?
- Improves Performance – Reduces latency by serving data from a closer, faster source.
- Reduces Database Load – Minimizes repeated queries to the database, reducing overhead.
- Handles High Traffic – Helps scale applications by reducing backend bottlenecks.
- Enhances User Experience – Faster responses lead to better user experience.

## Types of Cache
Caching can be implemented at different layers based on the system's needs:

### 1. Application Cache
- Stored in memory within the application.
- Example: Caching computed values inside a function.

### 2. Database Cache
- Reduces redundant queries by caching query results.
- Example: MySQL Query Cache, Redis as a caching layer for databases.

### 3. Content Delivery Network (CDN) Cache
- Stores static assets (CSS, JS, images) at edge locations closer to users.
- Example: Cloudflare, AWS CloudFront, Akamai.

### 4. Distributed Cache
- A shared cache across multiple servers, useful for large-scale applications.
- Example: Redis, Memcached.

### 5. Web Cache (Reverse Proxy Cache)
- Caches entire HTTP responses to reduce load on backend servers.
- Example: Nginx, Varnish Cache.

### 6. Client-Side Cache
- Caches data in the browser (cookies, local storage, service workers).
- Example: Browser caching CSS/JS files.

| Cache Type           | Description                                      | Examples                      | Pros                                      | Cons                                      |
|----------------------|------------------------------------------------|-------------------------------|-------------------------------------------|-------------------------------------------|
| **Application Cache**  | Stores frequently used data in app memory.  | `functools.lru_cache` in Python | Fast access, no extra setup needed.       | Limited by application memory.            |
| **Database Cache**   | Caches query results to reduce DB load.        | MySQL Query Cache, Redis       | Speeds up DB queries, reduces latency.   | May serve stale data, requires invalidation. |
| **CDN Cache**        | Caches static assets at edge locations.        | Cloudflare, AWS CloudFront    | Low latency, reduces server load.        | Best for static content only.            |
| **Distributed Cache**| Shared cache across multiple servers.          | Redis, Memcached              | Scales well, high availability.          | Needs proper eviction strategy.          |
| **Reverse Proxy Cache** | Caches HTTP responses to offload backend.  | Nginx, Varnish Cache          | Improves web performance, reduces load.  | Harder to invalidate dynamically.        |
| **Client-Side Cache** | Caches in browser (cookies, local storage).   | Service Workers, IndexedDB    | Reduces server calls, improves UX.       | Users may need to clear cache manually.  |

## Cache Invalidation Strategies
Since cached data can become outdated, cache invalidation strategies help maintain consistency.

### 1. Time-to-Live (TTL) Expiry
- Cache items expire after a set time (e.g., 60 seconds).
- Works well for periodically updated data.
- Example: API responses cached for 5 minutes.

### 2. Write-Through Cache
- Writes data to both the cache and database simultaneously.
- Ensures data consistency but adds write latency.
- Example: A user profile update is saved in both Redis and PostgreSQL.

### 3. Write-Back (Lazy Write) Cache
- Data is written to the cache first and asynchronously updated in the database.
- Faster writes but risks data loss if the cache crashes before syncing.

### 4. Cache Eviction (LRU, LFU, FIFO)
- Least Recently Used (LRU) – Removes the least recently accessed item.
- Least Frequently Used (LFU) – Removes the least accessed items over time.
- First-In-First-Out (FIFO) – Removes the oldest cached item first.

### 5. Manual Invalidation
- Developers explicitly remove or refresh cached data when needed.
- Example: Clearing product cache when inventory is updated.

| Strategy           | Description                                   | Pros                                      | Cons                                      | Best Use Case |
|--------------------|-----------------------------------------------|-------------------------------------------|-------------------------------------------|--------------|
| **TTL Expiry**     | Sets a time limit for cached data.            | Simple, automatic expiration.             | May serve stale data before expiry.       | API responses, session data. |
| **Write-Through**  | Writes data to cache and database at same time. | Ensures consistency, always fresh.       | Slower writes due to dual storage.        | User profiles, frequently updated data. |
| **Write-Back**     | Writes to cache first, then updates DB later.  | Faster writes, reduces DB load.          | Risk of data loss if cache fails.         | Analytics, logs, bulk writes. |
| **LRU (Least Recently Used)** | Removes least recently accessed items. | Efficient, prevents cache bloat.         | May remove needed data if not accessed often. | General-purpose caching. |
| **LFU (Least Frequently Used)** | Removes least accessed items over time. | Keeps most popular data in cache.        | Harder to implement, needs frequency tracking. | High-traffic APIs. |
| **FIFO (First-In-First-Out)** | Removes oldest cached items first.  | Simple and predictable.                   | Not always optimal for performance.       | Limited-memory caches. |
| **Manual Invalidation** | Explicitly removes or refreshes cache.    | Full control over updates.                | Requires additional logic and tracking.  | Dynamic content like product catalogs. |
