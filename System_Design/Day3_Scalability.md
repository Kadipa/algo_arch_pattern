# Four Pillars of System Design

1. **Performance**  
   - How efficiently the system responds.  
   - Depends on hardware + optimization.  

2. **Scalability**  
   - Can it grow from **100 users → 1M users**?  
   - Must handle millions of daily requests.  

3. **Reliability**  
   - What happens if backend or DB fails?  
   - Can it recover without data loss or downtime?  

4. **Security**  
   - Protection from attacks + disasters.  
   - Includes **disaster recovery** planning.  

---

# Example Challenge
- Simple architecture (without DNS).  
- Reflect on:  
  - Speed & responsiveness (CRUD ops).  
  - Handling **1M requests/day**.  
  - Failure recovery (backend, DB, or full outage).  
- Lesson: Don’t over-engineer. **Choose the right tools for the scale.**  

---

# Key Takeaway
- A good system design = **strong foundation** (like a house on rock, not sand).  
- Always consider: **Performance, Scalability, Reliability, Security**.  

---

Extended Resources: 

## Scalability in System Design

### What is Scalability?
- The ability of a system to handle increasing load (users, requests, data) without performance degradation.  
- Example: Growing from 100 users to 1 million users, or processing millions of daily requests.

---

### Types of Scalability
1. **Vertical Scaling (Scale Up)**  
   - Add more power (CPU, RAM) to a single machine.  
   - Simple, but limited by hardware capacity.  

2. **Horizontal Scaling (Scale Out)**  
   - Add more machines (servers, nodes) to distribute load.  
   - Enables handling very large-scale systems.  

---

### Key Considerations
- **Load Balancing** → Distribute requests evenly.  
- **Caching** → Reduce repeated computation and database hits.  
- **Database Scaling**  
  - Read replicas, sharding, partitioning.  
- **Stateless Services** → Easier to scale horizontally.  
- **Asynchronous Processing** → Use message queues for heavy tasks.  

---

### Trade-offs
- Vertical scaling = easier but limited.  
- Horizontal scaling = more powerful but adds complexity (consistency, synchronization).  

---

### Takeaway
Scalability ensures a system grows gracefully with demand.  
It’s not just about adding servers, but designing architecture that can evolve without breaking.



