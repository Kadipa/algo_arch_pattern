# Content Delivery Network (CDN)

A **Content Delivery Network (CDN)** is a globally distributed network of proxy servers that serve content from locations closer to the user.  
Typically, CDNs serve **static files** such as HTML, CSS, JavaScript, photos, and videos. Some CDNs (e.g., Amazon CloudFront) also support **dynamic content**.  

The site's **DNS resolution** directs clients to the correct server.

---

## Benefits of CDNs

CDNs improve performance in two main ways:
1. **Reduced Latency** – Users receive content from data centers geographically closer to them.
2. **Reduced Server Load** – The origin server offloads requests that the CDN fulfills.

---

## Types of CDNs

### Push CDNs
- Content is **uploaded directly** to the CDN when changes occur on the server.  
- The website owner is responsible for uploading and managing updates.  
- You can configure **expiration times** and **update schedules**.  
- Content is uploaded **only when new or changed**, minimizing traffic but maximizing storage.  

**Best for:**  
- Sites with **low traffic**.  
- Sites with content that does not change frequently.  
- Content is placed on the CDN once, instead of being re-fetched at intervals.  

---

### Pull CDNs
- Content is **pulled from the origin server** the first time a user requests it.  
- URLs are rewritten to point to the CDN.  
- The **first request may be slow**, but subsequent requests are fast since the content is cached.  
- Cached content is refreshed based on a **Time-to-Live (TTL)** setting.  

**Best for:**  
- Sites with **high traffic**.  
- Spreads out load since only recently-requested content is cached.  
- Minimizes CDN storage, but can create redundant traffic if files expire before being updated.  

---

## Disadvantages of CDNs
- **Cost**: CDN usage may become expensive depending on traffic volume.  
- **Stale Content**: Content may remain outdated until the TTL expires.  
- **URL Management**: Requires rewriting URLs to point to the CDN.  

