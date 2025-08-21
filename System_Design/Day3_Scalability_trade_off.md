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

Extended Resources: https://blog.umer-farooq.com/system-design-for-beginners-part-ii-understanding-the-3-tier-architecture-using-everyday-analogies-f2e6537d04af

# Trade off

## Performance Vs Scalabiltiy

- System is slow for a single user => performance problem
- System is fast for a single user, but slow for the heavy workloads => Scalability Issues

## Latency Vs Throughput

- Latency: time window to perform the action
- ThroughtPut: no of action performed at a unit







