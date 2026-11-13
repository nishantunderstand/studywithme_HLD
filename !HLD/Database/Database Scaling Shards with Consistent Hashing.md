https://www.instagram.com/p/Dau2p7qDz11/


System Design: Scaling Shards with Consistent Hashing!  
  
Basic database sharding setups fail when scaling out storage nodes. Relying on simple modulo routing like (User ID % number of shards) breaks down the moment you add a new machine. Because changing the divisor alters the target mapping for almost every key, it forces an expensive, catastrophic data migration across nearly the entire cluster.  
  
Never trigger cluster-wide data reshuffling just to increase database capacity. Instead, implement consistent hashing by mapping both user IDs and database nodes onto a virtual circular ring. Requests route clockwise to the first available shard they encounter, ensuring that provisioning a new node only intercepts a tiny fraction of keys from its immediate neighbor.  
  
This distribution pattern shields databases from massive re-sharding overhead, ensures high availability during cluster expansion, and keeps data movement minimal and mathematically optimal.