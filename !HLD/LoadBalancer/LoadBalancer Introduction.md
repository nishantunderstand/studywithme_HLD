LoadBalancer Types Why 
https://www.instagram.com/p/Dazuq4rhE9b/



- Traffic
- Server Overlaod
- Example : Resturant Manager 



"A Load Balancer distributes incoming traffic across multiple backend servers so no single server becomes a bottleneck or point of failure.  
  
Four routing algorithms — Round Robin: equal distribution in rotation. Least Connections: routes to server with fewest active connections. IP Hash: same user always goes to same server — for session consistency. Weighted: powerful servers get proportionally more traffic.  
  
Two layers — L4: transport layer, routes by IP and port, fast and lightweight. L7: application layer, reads HTTP content, routes intelligently — /payments to Payment Service, /users to User Service. Nginx is L7, AWS ELB supports both.  
  
Health Checks — Load Balancer pings each server periodically. No response — removed from rotation automatically until recovery.  
  
Critical production consideration — Load Balancer itself is a single point of failure. Solved with Active-Passive or Active-Active multiple Load Balancer setups. Netflix, Amazon, Instagram all use multiple load balancing layers."


---


https://www.instagram.com/p/Db5REAoCm77/
