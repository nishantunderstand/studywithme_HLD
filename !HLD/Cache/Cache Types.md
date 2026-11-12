Types of Cache (Hibernate) : 
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

In CPU Architecture : 
1. L1 Cache
2. L2 Cache
3. L3 Cache

----
[[Cache CPU]]
