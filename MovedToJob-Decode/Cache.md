

![[Thread-InHiererary.png]]

 **locality of reference**,
Types
1. **Spatial Locality**
2. **Temporal Locality:**




## Cache Line Organization 🤔🤔🤔 
The cache lines do not have a fixed address, allowing the cache to store data from various locations in memory.

Types
1. Fully Associated
2. Direct Mapped
3. Self Associated










[[Redis]]

---

Cache
Cache vs Traditional DB
What 
Why 

Cache Store 
Cache Hit
Cache Miss
Cache Hit Ratio 
Meaning 
Significance
Calculate 

https://www.instagram.com/p/DaU2LHuhjXA/

---
Types of Cache

1. Application / ORM Cache (Local)
	1. L1 Cache 
		Session / Persistence Context (Hibernate /JPA Terminology)
		Single Session
		Enabled By Default 
	2. L2 Cache
		SessionFactory / EntityManagerFactory (Hibernate /JPA Terminology)
		Across Multiple Session / Shared 
		You need to Configure
			Caffeine
			Ehcache
			Hazelcast
2. Distributed Cache (Shared)
	Redis

---
Hibernate L1 vs L2 Cache
Hibernate vs Redis Cache

---


Cache Population Strategies
1. Cache-Aside (Lazy Loading)
2. Read-Through
3. Write-Through
4. Write-Behind

Cache Aside Pattern												
Pro 
Cons
Stale Data								
https://www.instagram.com/p/DaW1bKzB-OR/

Cache-Aside Race Conditions

---

Cache Aside Pattern 
Read Through 
Write Through 

DB vs Cache 
Which is updated first ?
How to decide ?

Banking Application / No Stale Data : Write Through
https://www.instagram.com/p/DacLvBEBkq-/

---

Cache Eviction Policies :
Cache needs space
Which entry should be removed?
1. LRU : Least Recently Used
2. LFU : Least Frequently Used
3. FIFO : First In First Out
4. TTL : Time To Live

**Expiration/TTL** → Entry becomes invalid after a certain time.


---




----

Cache Invalidation vs Cache Stampede vs Cache Warming
- Cache Invalidation 
- Cache Stampede / Thundering Herd / Dogpile effect 
- Cache Warming
- https://www.instagram.com/p/DaiNiicBhsj/


Hot / Popular Key 
1. One / Few Popular Key Expired : Cache Breakdown / Cache Stampde
2. Multiple Popular Key Expired Simuatlentously : Cache Avalanche

Solution :
- Request Coalescing / single-flight
- Distributed Lock
- Cache Warming
- Background Refresh
- Stale-While-Revalidate
- TTL Jitter


Cache Stampede / Thundering Herd / Dogpile effect

Thundering Herd Problem
https://www.instagram.com/reels/Db8YSsrzb3q/


TTL 
Solution : 
1. Request Coaleasing (Single Request)
2. Cache Warming
[Thundering Herd Problem - The Codergirlie](https://www.instagram.com/p/DW9D_PWkfsJ/)

Cache Avalanche
Solution : 
1. TTL Jitter
2. Cache warming
3. Multiple cache layers
4. Circuit breaker
5. Rate limiting
6. Fallback

What is Cache Avalanche? How different From Cache Stampede ?



---

Cache Penetration  : Data does NOT exist
- Negative Caching
- Bloom Filter
- Input Validation
- Rate Limiting


Cache Penetration vs Cache Breakdown/Stampede vs Cache Avalanche

---





Types of Cache 
1. L1 Cache
2. L2 Cache
3. L3 Cache

Transalation Lookaside Buffer

OS :
Page Cache
FileSystem Cache

Inode cache