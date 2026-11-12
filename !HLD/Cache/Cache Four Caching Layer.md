
https://www.instagram.com/p/Dbiuy94zo1e/


The four common caching layers  
  
1. Browser cache: static assets like images, CSS, and JS stored locally via Cache Control headers. Zero network calls on repeat visits.  
  
2. CDN: your content cached on edge servers near the user. Cuts latency before the request even reaches your backend.  
  
3. App cache (Redis or Memcached): computed results held in memory. This is the layer interviewers dig into the most, so know it cold.  

4. Database cache: buffer pools keep hot data in RAM while cold data waits on disk.  

Worth noting: these four cover most interview questions, but there are others too, like DNS caching and reverse proxy caching.  
  
The follow up question they’ll ask is about eviction policy. (cache invalidation, not caching itself, is the genuinely hard part), caching strategies etc.


---
https://www.instagram.com/p/DRKVrPIkk6b/
CDN 
Edge Server


----

Where Caching is Happening : 
1. Browser Cache (Client Side ) | ETag
2. CDN Cache (Edge Layer) | CloudFare , AWS CloudFrount , Akamai
3. Application / Server Side Cache (Redis / MemCached)
4. Database Cache | MySQL InnoDB BufferPool, PostgreSQL Shared Buffers

----

# 2. Understand the four caching layers

![브라우저 캐시 완벽 가이드 - HTTP 캐싱의 모든 것 | Manuel](https://images.openai.com/static-rsc-4/CLrZMwDQGiIlWXy8E3JRPwSJ25W9BGcP6aCO6RYsZC7yNB54fAJeSTZ7ZmPJL3vQ-umi3WDDA6bE0YDQfvJyg31lGTZlWxU0X_uZqObThtF5g3fj6GPbog5pd7Vo3S9FccCgRRxFX08ZOAT1CkNMXPiVJMr3zdLlNJgabT8hT4Y?purpose=inline)

1. Browser Cache (Client Side)

Stores static resources on the user's device.
Examples: HTML, CSS, JavaScript, images, fonts.
Technology: HTTP Cache-Control, ETag, Expires.

Example: When you revisit a website, the browser can reuse its previously downloaded CSS instead of downloading it again.

![Part 4 : System Design :- Diving with CAP Theorem, Consistency, Designing distributed systems | by TechwidSush | Medium](https://images.openai.com/static-rsc-4/RxripHSkSlfregxo404xO_WhZMbsVg3dCMPwGX95ldJPn2CfonNDH7RGypq7COtczT3OOouZcZlPnLlQAlusU168nMz-ocwRl8z6hXi8qZd0uB09smmlHNOQYYAW5W1bboMo96cePGJ2FtJcXujDKUxjuwMcXHvYHYYsMuvKqBM?purpose=inline)

2. CDN Cache (Edge Layer)

Stores content on geographically distributed edge servers.
Examples: Images, videos, CSS, JS, downloadable files.
Technology: Cloudflare, AWS CloudFront, Akamai.
Example: A user in Delhi gets an image from a nearby CDN edge instead of your origin server in another country.

!["Day 4: Caching with Redis and Spring Boot" | Venkatesh Pardeshi posted on the topic | LinkedIn](https://images.openai.com/static-rsc-4/yw1SUiQvEDaZDX-y2o5B2Rm343uds0enjuSuyz1OttQP5gfB4vtRbanbpyDdhno5BrTLRdUetUAQZaGbGYMTb1ULT1ntZ8HhI3VfbkaWT1fNSI3n6jMTdu9NjIs3BwJqNj6MulKncfcRBKx3T-Ct4KjPCO3Xv8yRKIrpO5Z-Oa0?purpose=inline)

3. Application / Server-Side Cache
Stores frequently accessed or expensive-to-compute data in memory.
Examples: User profile, product details, permissions, API responses.
Technology: Redis, Memcached, Caffeine, Ehcache.
Example: Instead of querying MySQL every time for a user's profile, Spring Boot fetches it from Redis.

![PPT - CS422 Principles of Database Systems Buffer Management PowerPoint Presentation - ID:9189215](https://images.openai.com/static-rsc-4/ldl3c6VcMJQNohDPyB2wOtuxigmWi1WL2yV3Aqob63v9aQDpas4maEZG7rYI6iQr3K-M4yCo0PPjLehM1VzRK7PA5mXMz8o8eS1zi7ZbCyQkDy4CPzcmQyVgbPWEw-9muqAdAiFRaeCBYMOYfKnbrmMLZnjtDtxbwUG238-W6kc?purpose=inline)

4. Database Cache
The database keeps frequently accessed data and index pages in memory.
Examples: Data pages, index pages.
Technology: MySQL InnoDB Buffer Pool, PostgreSQL shared buffers.
Example: Repeated queries can read hot data from RAM instead of accessing disk.


---


```
Types of Cache
│
├── 1. Client-Side Cache
│   └── Browser Cache
│
├── 2. Edge / Network Cache
│   ├── CDN Cache
│   ├── Reverse Proxy Cache
│   └── DNS Cache
│
├── 3. Application / Server-Side Cache
│   ├── Local / In-Process Cache
│   │   ├── Caffeine
│   │   └── Ehcache
│   │
│   ├── ORM Cache (Hibernate)
│   │   ├── L1 Cache
│   │   └── L2 Cache
│   │
│   └── Distributed Cache
│       ├── Redis
│       └── Memcached
│
└── 4. Database Cache
    ├── Buffer Pool
    └── Shared Buffers
```