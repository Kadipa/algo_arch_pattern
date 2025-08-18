# Scalability Notes (Harvard Lecture)

## 1. Vertical Scaling (Scaling Up)
- **Definition:** Increasing the power of a single machine (CPU, RAM, SSD, etc.).  
- **Pros:**
  - Simple to implement
  - No code changes required
- **Cons:**
  - Hardware has a limit (ceiling)
  - Expensive upgrades
  - Single point of failure  
- **Use Case:** Quick solution for small systems

---

## 2. Horizontal Scaling (Scaling Out)
- **Definition:** Adding more machines/instances to handle load.  
- **Pros:**
  - Virtually unlimited growth
  - Fault tolerance (if one machine fails, others continue)
- **Cons:**
  - Requires distributed systems design
  - Harder to maintain consistency
- **Use Case:** Large-scale web apps (Google, Facebook)

---

## 3. Caching
- **Definition:** Storing frequently accessed data in faster storage (memory).  
- **Types of caching:**
  - **Client-side cache** (browser, mobile app)
  - **CDN** (edge caching static content)
  - **Server-side cache** (Redis, Memcached)  
- **Pros:**
  - Reduces database load
  - Improves response time
- **Cons:**
  - Cache invalidation is tricky
  - Stale data possible  
- **Use Case:** API responses, static files, session storage

---

## 4. Load Balancing
- **Definition:** Distributing incoming requests across multiple servers.  
- **Strategies:**
  - Round Robin
  - Least Connections
  - IP Hashing  
- **Pros:**
  - Prevents single server overload
  - Improves availability  
- **Cons:**
  - Adds complexity
  - Load balancer itself can become a bottleneck  
- **Use Case:** Web servers, microservices clusters

---

## 5. Database Partitioning (Sharding)
- **Definition:** Splitting a large database into smaller, more manageable pieces.  
- **Types:**
  - **Horizontal partitioning (Sharding):** Rows split by key (e.g., user_id)  
  - **Vertical partitioning:** Splitting tables by columns (e.g., separating logs from user profile data)  
- **Pros:**
  - Handles very large datasets
  - Improves query performance if done right  
- **Cons:**
  - Complex to implement
  - Cross-shard queries are expensive  
- **Use Case:** Social media feeds, e-commerce user orders

---

## 🔑 Quick Visual Mental Model
- **Vertical scaling = bigger computer**  
- **Horizontal scaling = more computers**  
- **Caching = shortcuts to avoid repeating work**  
- **Load balancing = traffic cop**  
- **Partitioning = split the data into smaller neighborhoods**  

---

## 📚 References
- Harvard CS Scalable Systems Lecture
- [System Design Primer](https://github.com/donnemartin/system-design-primer)
