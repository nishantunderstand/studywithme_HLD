
Restaurant Analogy
- The Host  :  Load Balancer
- The Waiter : Backend Server
- The Customer : Incoming Request





LoadBalancer Algorithm 
1. Round Robin  : Fair Turn / Identiacial Server 
2. Least Connections : Fair Work
3. IP Hashed (Sticky Session)
4. Weighted Load Balancing (By Capacity) : Different Capacity 

https://www.instagram.com/p/Da1uAYbh70F/



"Load Balancing Algorithms determine how requests are distributed across backend servers. Three most common:  
  
Round Robin — requests distributed sequentially in rotation. Works well when all servers have similar capacity and request processing times are equal. Simple and predictable.  
  
Least Connections — every new request goes to the server with fewest active connections. Smarter for dynamic workloads where some requests take longer. Ideal for long-lived connections like WebSockets and database sessions where round-robin causes uneven distribution over time.  
  
Weighted Load Balancing — each server gets a weight proportional to its capacity. 8-core server gets weight 8, 2-core server gets weight 2 — traffic distributed in that ratio. Right choice for heterogeneous server fleets where equal distribution would overload weaker machines.  
  
Production systems combine all three — Round Robin for stateless APIs, Least Connections for session workloads, Weighted for mixed hardware generations.  
  
Best algorithm? Always depends on workload type and server characteristics."












---
https://www.youtube.com/watch?v=dBmxNsS3BGE

Types of Load Balancer
Dynamic 
1. Least Connection
2. Least Time

Static
1. RoundRobin
	1. Weighted RoundRobin
	2. Sticky RoundRobin
2. Hash


![[LoadBalancer 1 Algorithm.png]]