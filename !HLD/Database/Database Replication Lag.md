- Database Replication Lag
![[Database 6.png]]

- Sync Replication
- Async Replication
- Failover vs Split Brain
- Delay 


![[Database 5.png]]

Master 
Slave 
What happen if Master Dies ?
Conesus Algorithm
Read 
Write 

https://www.instagram.com/reel/DY_hXYXBTBB/



🧑 💻 "Replication Lag is the delay between a write on the master and that write appearing on replicas. In async replication — used by Instagram and Twitter — the master confirms immediately, creating this lag window.  
  
Most common symptom — user posts, refreshes, doesn't see it. Fixed with Read Your Own Writes — routing that user's immediate reads back to the master. Monotonic Reads problem — user sees data on Replica A, next request hits Replica B which is further behind, data disappears. Fixed with Sticky Sessions.  
  
Failover — when master crashes, a monitoring agent detects failure, selects the most up-to-date replica by replication position, and promotes it to master. App servers redirect via DNS update or virtual IP. Key risk — writes acknowledged by the old master but not yet replicated are permanently lost.  
  
Split Brain — network partition causes two nodes to both believe they are master simultaneously. Both accept writes independently. Data diverges, corruption follows. Prevented through consensus mechanisms like Raft or Paxos — requiring majority quorum before any node becomes master. Fencing tokens invalidate the old master's write access immediately."  


---
Split Brain
Quorom
That's why Replica is Odd Number 

https://www.instagram.com/reels/De6-qIYyKzO/