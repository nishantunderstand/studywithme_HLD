https://www.youtube.com/watch?v=LQuuoHTyYz8


![[LoadBalancer 2.png]]

Types of LoadBalancer 
- Hardware
- Software
- CloudBased
- Global Level LoadBalancer

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

- HTTP/API → L7  
- TCP/UDP → L4

[[LoadBalancer L4 vs L7]]


![[LoadBalancer 3.png]]