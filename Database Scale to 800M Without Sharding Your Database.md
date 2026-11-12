[[Database]]
https://www.instagram.com/p/DfSAn-WP_fS/


When juniors see massive scale, their first instinct is to immediately shard the database.  
  
But OpenAI handles millions of queries per second for 800 million ChatGPT users using a single primary PostgreSQL database and ~50 read replicas.  
  
Why didn't they shard? Because sharding existing workloads requires rewriting hundreds of application endpoints—months or years of work.  
  
Instead, they engineered around Postgres's weak spots (Save this for your next system design interview 📌):  
  
1️⃣ Connection Storms: They run PgBouncer on Kubernetes to drop connection time from 50ms down to 5ms.  
2️⃣ Cache-Miss Storms: They use cache locking. If a cache misses, only ONE request hits the database while the rest wait in line.  
3️⃣ Write Pressure: They strictly rate-limit backfills and use lazy writes to prevent MVCC (Multi-Version Concurrency Control) bloat.  
  
By moving only their hyper-write-heavy workloads to Cosmos DB, they kept their core architecture unsharded, hitting p99 latency in the low double-digit milliseconds.  
  
The Technical Trap 🪤:  
Running a single primary with 50 read replicas works, but it creates a massive physical bottleneck. The primary database has to stream its WAL (Write-Ahead Log) to every single replica simultaneously.  
  
If ChatGPT scales to 150 read replicas, the primary's network bandwidth and CPU will literally melt just from replicating its own data.  
  
How do you scale past 100 read replicas without suffocating the single primary database? Drop your architecture fix in the comments. 👇


