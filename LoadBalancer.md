LoadBalancer Types Why 
https://www.instagram.com/p/Dazuq4rhE9b/

LoadBalancer Algorithm  🤔🤔🤔
1. Round Robin  
2. Least Connections 
3. IP Hashed 
4. Weighted Load Balancing

https://www.instagram.com/p/Da1uAYbh70F/

L4 vs L7 LoadBalancer

Nginix : L4 (Fast)
AWS ELP : Both 

[[OSI]]

https://www.instagram.com/p/Da4eQb5Bphk/


---
https://www.youtube.com/watch?v=LQuuoHTyYz8
Types of LoadBalancer 
Hardware
Software
CloudBased

Global Level LoadBalancer

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

---

```
AWS Elastic Load Balancing ELB
        │
        ├── ALB → Layer 7
        │         HTTP / HTTPS
        │         Path / Host routing
        │
        ├── NLB → Layer 4
        │         TCP / UDP / TLS
        │
        └── GWLB → Gateway Load Balancer
                  Network/security appliances
```


|             |         ALB         |           NLB            |
| :---------: | :-----------------: | :----------------------: |
|    Layer    |       **L7**        |          **L4**          |
|  Protocol   |     HTTP/HTTPS      |       TCP/UDP/TLS        |
|   Routing   | Path, host, headers |    IP/port/connection    |
| Typical use | REST APIs, web apps | High-performance TCP/UDP |


**HTTP/API → L7**  
**TCP/UDP → L4**
