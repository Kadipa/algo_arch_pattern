# Domain Name System (DNS)

## What is DNS?
The **Domain Name System (DNS)** translates a human-readable domain name (e.g., `www.example.com`) into an IP address.  
It is hierarchical, starting from root authoritative servers down to local resolvers.

## How DNS Works
- Your **router or ISP** provides information about which DNS server(s) to contact.
- **Lower-level DNS servers cache** mappings for faster lookups, but caches can become stale due to propagation delays.
- Results are cached by:
  - **Browser**
  - **Operating System**
  - **DNS Resolvers**
- Caching duration is determined by **TTL (Time to Live)**.

## Common DNS Records
- **NS (Name Server):** Specifies the DNS servers for a domain/subdomain.
- **MX (Mail Exchange):** Specifies mail servers for email delivery.
- **A (Address):** Maps a domain name to an IPv4 address.
- **CNAME (Canonical Name):** Points a domain name to another domain name or record (e.g., `example.com → www.example.com`).

## Managed DNS Services
Examples: **Cloudflare**, **AWS Route 53**  
They provide advanced routing methods:
- Weighted round robin
- Maintenance-based routing (skip unhealthy servers)
- Load balancing across clusters
- A/B testing
- Latency-based routing
- Geolocation-based routing

## Disadvantages of DNS
- **Lookup Delay:** DNS lookups introduce a slight delay, but caching mitigates this.
- **Management Complexity:** Requires infrastructure and coordination by ISPs, governments, and large companies.
- **Vulnerability to Attacks:**
  - DNS services have been targeted by **DDoS attacks**.
  - Example: Outages preventing access to websites (e.g., Twitter) unless the user knew the raw IP address.

## Key Takeaways
- DNS is **critical infrastructure** for the internet.
- Caching reduces lookup delays but can cause stale results.
- Managed DNS services enhance performance and reliability.
- Security threats (like **DDoS attacks**) highlight DNS as a major target.

---

**Sources & Further Reading:**
- DNS architecture (Wikipedia)
- DNS articles