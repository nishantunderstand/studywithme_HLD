- Type
- Hash-Based Sharding 
	- Even Distribution
	- Not Suitable For Range Based Query
- Range-Based Sharding
	- Range Based Distribution
	- Hot Partition 
- Hot Partitions
https://www.instagram.com/p/DZE5iWxh0ub/

![[Database 2.png]]



🧑‍💻 Hash-Based Sharding and Range-Based Sharding are two common database partitioning strategies.  
  
In Hash-Based Sharding, a hash function decides which shard stores the data. A common approach is user_id % number_of_shards. This distributes data evenly and prevents shard overload. The downside is that range queries become inefficient because related data may exist across multiple shards.  
  
In Range-Based Sharding, data is divided using ID ranges or timestamps. This makes range queries extremely fast because related data stays together. However, it can create Hot Partitions, where one shard receives most of the traffic while others remain underutilized.  
  
Hash-Based Sharding is best for balanced load distribution. Range-Based Sharding is best for range-based queries and analytics.  
  