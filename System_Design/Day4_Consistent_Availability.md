# Consistency and Availability Patterns

## Consistency Patterns
Consistency = every read receives the most recent write or an error.

### Weak Consistency
- After a write, reads **may or may not see it**.  
- Best-effort approach.  
- Example: **memcached**, VoIP, video chat, multiplayer games.  
- Missed data during disconnection is lost.

### Eventual Consistency
- After a write, reads will **eventually see it** (async replication).  
- Example: **DNS**, email.  
- Works well in **highly available systems**.

### Strong Consistency
- After a write, reads will **always see it** (sync replication).  
- Example: **file systems**, RDBMS.  
- Needed for **transactions**.

---

## Availability Patterns

### Fail-over
**Active-Passive**
- Only active server handles traffic.  
- Passive takes over if active fails (hot or cold standby).  
- AKA master-slave failover.

**Active-Active**
- Both servers handle traffic and share load.  
- Requires DNS/app logic awareness.  
- AKA master-master failover.  

**Disadvantages**
- More hardware, complexity.  
- Possible data loss if failover happens before replication.

### Replication
- **Master-Slave Replication**  
- **Master-Master Replication**

---

## Availability in Numbers
Measured in "number of 9s" uptime.

- **99.9% (three 9s)**  
  - Yearly downtime: ~8h 46m  
  - Daily downtime: ~1m 26s  

- **99.99% (four 9s)**  
  - Yearly downtime: ~52m  
  - Daily downtime: ~8.6s  

---

## Availability in Systems

### In Sequence
- Total availability = multiply component availabilities.  
- Example: two 99.9% → 99.8%.  

### In Parallel
- Total availability = `1 - (1 - A1) * (1 - A2)`  
- Example: two 99.9% → 99.9999%.
