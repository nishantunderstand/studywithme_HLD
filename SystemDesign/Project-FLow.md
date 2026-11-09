Client / Frontend / Mobile App
        ↓
DNS / CDN (optional)
        ↓
AWS Load Balancer (ALB / NLB)
        ↓
API Gateway
        ↓
Authentication / Authorization
   - JWT Validation
   - OAuth2 / OpenID Connect
   - Rate Limiting
        ↓
Spring Security Filter Chain
   - UsernamePasswordAuthenticationFilter (login flow only)
   - JWT Authentication Filter
   - SecurityContextHolder populated
        ↓
DispatcherServlet
        ↓
HandlerMapping
        ↓
Controller
        ↓
Facade (optional)
        ↓
Service Layer
        ↓
Repository Layer
        ↓
Database / Cache / External APIs
        ↓
Response DTO Transformer / Mapper
        ↓
Controller ResponseEntity
        ↓
API Gateway
        ↓
Client



Interceptor
JWT

Transaction Annotation
Redis 
KAFKA