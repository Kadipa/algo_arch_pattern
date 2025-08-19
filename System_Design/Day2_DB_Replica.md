# Database Replication

## Definition
Database replication is the process of creating and maintaining copies of the same database across multiple servers to ensure reliability, availability, and performance.

## Goals
- High availability: If one replica fails, another can take over.
- Load balancing: Read operations can be distributed across replicas.
- Disaster recovery: Backups and geo-redundancy for fault tolerance.

## Types
- **Master–Slave (Primary–Replica)**: A single primary handles writes, replicas handle reads.
- **Multi-Master**: Multiple nodes can accept writes, requiring conflict resolution.
- **Synchronous vs. Asynchronous**:
  - *Synchronous*: Ensures consistency but increases latency.
  - *Asynchronous*: Faster, but risks losing the most recent writes during failure.

## Trade-offs
- Consistency vs. latency.
- Complexity increases with more replicas, especially across regions.

---

# CAP Theorem

## Definition
The CAP theorem states that a distributed system can only provide two of the following three guarantees simultaneously:

1. **Consistency (C)**  
   Every read receives the most recent write, ensuring all nodes return the same data.

2. **Availability (A)**  
   Every request receives a response, even if it is not the most recent data.

3. **Partition Tolerance (P)**  
   The system continues to operate despite network partitions or communication failures between nodes.

## Trade-Off
- Network partitions are unavoidable in distributed systems.
- As a result, designers must choose between:
  - **CP Systems (Consistency + Partition Tolerance)**: Prioritize consistency, may sacrifice availability.  
    - Example: HBase, MongoDB (strong consistency mode).
  - **AP Systems (Availability + Partition Tolerance)**: Prioritize availability, may serve stale data.  
    - Example: Cassandra, DynamoDB, CouchDB.
  - **CA Systems (Consistency + Availability)**: Only feasible without network partitions, typically single-node databases.

## Practical Examples of CAP Trade-offs

### 1. Prioritizing Consistency (CP)
- **Financial Transactions**: Banking systems (balances, payrolls, stock trades) require strict consistency to avoid double-spending or incorrect trades.  
- **Healthcare Records**: Patient and medical records must remain accurate and up to date.  
- **Ticket Booking**: Airline and event systems must prevent overbooking by ensuring consistent seat availability.  

### 2. Prioritizing Availability (AP)
- **Social Media**: Platforms like Facebook or Twitter allow posting and interaction even if some data is slightly stale.  
- **Content Delivery Networks (CDNs)**: Deliver content quickly, even if nodes are not fully synchronized.  
- **Streaming Services**: Services such as Netflix prioritize continuous playback over strict consistency.  

### 3. Balancing Consistency and Availability (CA)
- **Small-scale Web Applications**: In environments where network partitions are rare, both guarantees can often be maintained.  
- **Real-time Collaboration Tools**: Applications like collaborative editors balance consistency and availability within limited scopes.  

### 4. Illustrative Trade-offs
- **Inventory Management**: During a network partition, the system may either:
  - Prioritize **consistency**: show the most accurate stock levels, or  
  - Prioritize **availability**: allow the purchase even if inventory is slightly outdated.  

- **Online Shopping Carts**: During a partition, the system may either:
  - Prioritize **availability**: show items immediately in the cart, or  
  - Prioritize **consistency**: delay updates until the system is synchronized.  

---

### Key Takeaway
The CAP theorem emphasizes that distributed systems must make trade-offs. The right choice depends on application requirements:
- **CP** for financial, healthcare, and booking systems.  
- **AP** for user-facing platforms prioritizing responsiveness.  
- **CA** for small-scale or partition-rare environments.  
