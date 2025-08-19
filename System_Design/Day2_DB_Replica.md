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


