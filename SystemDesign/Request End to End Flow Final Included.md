Talk to Mukul For Better Undestanding.


![[System-Desgin-Flow-End-To-End Image.png]]

---


![[Kubernetes Request Flow Infographic Images.png]]


![[Client DNS Image.png]]


```
                 INCOMING HTTP REQUEST
                          |
                          v
                  +----------------+
                  |     Client     |
                  | Browser/Postman|
                  +----------------+
                          |
                          v
                  +----------------+
                  |   DNS + HTTPS  |
                  +----------------+
                          |
                          v
                  +----------------+
                  | AWS ALB /      |
                  | Kubernetes     |
                  | Ingress        |
                  +----------------+
                          |
                          v
                  +----------------+
                  | Kubernetes     |
                  | Service        |
                  +----------------+
                          |
                          v
                  +----------------+
                  | EndpointSlice  |
                  | / Pod Routing  |
                  +----------------+
                          |
                          v
              +---------------------------+
              |       Kubernetes Pod      |
              |                           |
              |  +---------------------+  |
              |  | Docker Container    |  |
              |  | Spring Boot App     |  |
              |  +---------------------+  |
              +---------------------------+
                          |
                          v
                  +----------------+
                  | Embedded       |
                  | Tomcat         |
                  +----------------+
                          |
                          v
                  +----------------+
                  | Servlet Filter  |
                  | Chain           |
                  +----------------+
                          |
                          v
                  +----------------+
                  | Spring Security|
                  | Authentication |
                  | Authorization   |
                  +----------------+
                          |
                          v
                  +----------------+
                  | DispatcherServlet|
                  +----------------+
                          |
                          v
                  +----------------+
                  | HandlerMapping |
                  | Find Controller|
                  +----------------+
                          |
                          v
                  +----------------+
                  | Interceptor    |
                  | preHandle()    |
                  +----------------+
                          |
                          v
                  +----------------+
                  | Controller     |
                  | @RestController|
                  +----------------+
                          |
                          v
                  +----------------+
                  | Validation     |
                  | @Valid         |
                  +----------------+
                          |
                          v
                  +----------------+
                  | Service Layer  |
                  | Business Logic |
                  +----------------+
                          |
                          v
                  +----------------+
                  | Repository     |
                  | JPA / Hibernate|
                  +----------------+
                          |
                          v
                  +----------------+
                  | Database       |
                  | MySQL / RDS    |
                  +----------------+

              RESPONSE FLOW  <----------------

Database → Repository → Service → Controller
        → HttpMessageConverter (JSON)
        → Interceptor completion hooks
        → Servlet Filter Chain returns
        → Tomcat → Pod → Network → Client
```