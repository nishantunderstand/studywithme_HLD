
https://www.instagram.com/p/DYPZsTCzhCX/
Replication means copying the same data across multiple servers.  
Sharding means splitting data across multiple servers.  
  
Both help databases scale, but in completely different ways.  
  
If your system struggles because millions of users are reading data simultaneously, replication helps distribute read traffic and improves availability.  
  
But if a single database can’t handle the growing dataset or write throughput anymore, replication won’t save you. That’s when sharding becomes necessary.  
  
In short:  
Replication solves read scaling  
Sharding solves write + storage scaling

![[Pasted image 20261113013953.png]]


![[Pasted image 20261113014006.png]]
