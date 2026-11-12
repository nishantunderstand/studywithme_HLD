One Database : BottleNeck 
Database Replication

![[Database 3.png]]

- What is Database Replication ?
- Master-Slave Architecture

Database 
1. Write : Master
2. Read :  Replica 

![[Database 4.png]]

Why Use Replication ?
- Read Scaling
- High Availability
- Disaster Recovery
- Geographic Low Latency.  


Database Replication
Read, Operation +  Write, Insert, Delete Operation
Master-Slave Architecture
Synchronous vs Asynchronous replication 
https://www.instagram.com/reel/DY7M28ghL5N/


🧑 💻 "Database Replication copies data from a master to replica servers continuously. Master handles all writes, replicas handle reads — distributing load and scaling read throughput.  
  
Benefits: read scaling, high availability, disaster recovery, geographic low latency.  
  
Synchronous replication — master waits for replica ACK before confirming success. Zero data loss but slower. Used in banking.  
  
Asynchronous replication — master confirms immediately, replicas update shortly after. Faster but small data loss risk. Used by Instagram and Twitter.  
  
Main challenge is Replication Lag — replicas falling behind master. Solved with Read Your Own Writes strategy. Another risk is Split Brain — two nodes both believing they are master — handled through consensus mechanisms."