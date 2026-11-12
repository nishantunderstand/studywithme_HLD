
https://www.instagram.com/p/Dc_W2zRSquw/


Reverse Proxy vs Load Balancer vs API Gateway ; three terms you’ll hear constantly in system design interviews, but they solve different problems.  
  
Reverse Proxy —> forwards requests to backend servers  
Load Balancer —> distributes traffic across multiple instances  
API Gateway —> provides a single entry point and handles routing, authentication, rate limiting, and other cross-cutting concerns  
  
One important nuance: API Gateway —> Load Balancer —> Reverse Proxy is one possible architecture, not a universal sequence. In real systems, these components can be arranged differently depending on the architecture. For example, a load balancer can also sit in front of API gateways to distribute traffic across multiple gateway instances.