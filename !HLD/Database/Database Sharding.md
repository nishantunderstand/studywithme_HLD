- Database Partitioning 
- Horizontal  : Sharding 
- Vertitcal  : ??
- Data is Splited , Not Copied
- One Database : Bottleneck
- 🤔🤔🤔 But Issue is I still one Database || What if that database fail ??
- Read And Write 
- Database Sharding
- Shards 
- Independent Database 
- Share the load 
- Split Based on Key i.e. shard key 

- Why Sharding? 
![[Database 1.png]]


https://www.instagram.com/reel/DZCJ2XVhAXr/


- Hotspot Shards 
- Cross Shard Queries
- Database Problem
- Read : Replication 
- Write : Sharding 
- Database Query Performance  🤔🤔🤔 
- when a shard grows too large, splitting it requires significant data migration

---




Exact Interview Answer ⤵️  

🧑‍💻 "Database Sharding is the process of horizontally partitioning a large database into multiple smaller, independent databases called shards — where each shard holds a subset of the total data, typically split by a shard key.  
  
The core motivation is that Replication alone cannot solve write scalability. In a master-replica setup, all writes still go to a single master — adding replicas only helps with read throughput. When write volume or data volume exceeds what a single machine can handle, sharding becomes necessary.  
  
Each shard operates as a fully independent database — with its own tables, indexes, RAM, CPU, and storage. For example, a Users table with 1 billion rows could be split across 4 shards by User ID range: Shard 1 handles IDs 1 to 250 million, Shard 2 handles 250 to 500 million, and so on.  
  
The key benefits are Write Scaling — distributing writes across shards so throughput scales horizontally, theoretically multiplying write capacity by the number of shards. Storage Scaling — eliminating single machine storage limits by spreading data across multiple servers. And Query Performance — smaller per-shard indexes fit entirely in RAM, making reads significantly faster. Backups also become faster and parallelizable.  
  
The main challenges with sharding are Cross-Shard Queries — joins across shards are expensive and often require application-level handling. Hotspot Shards — poor shard key choice can route disproportionate traffic to one shard, defeating the purpose. And Resharding Complexity — when a shard grows too large, splitting it requires significant data migration."  
  
