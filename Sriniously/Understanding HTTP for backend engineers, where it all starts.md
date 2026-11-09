
https://www.youtube.com/watch?v=a3C1DMswClQ&list=PLui3EUkuMTPgZcV0QhQrOcwMPcBCcd_Q1&index=5

HTTP Protocols

1. Stateless
2. Client-Server Model

HTTP and HTTPS 
TLS SSL 
TLS Encryption

![[Understanding HTTP for backend engineers, where it all starts 2026-11-01 22.15.07.excalidraw]]


TCP
TCP HandShake
UDP
OSI Model 
Layer 7
Network Layer


HTTP 1 2 3

Request Request Header 

![[Sriniously-5-HTTTPs.png]]

- Why do we need this Request & Response Header ?
- Understand by Parcel Example 

Types of Header
1. Request Header 
	User-Agent
	Authorization
	Cookie
	Accept
2. General Header
	Data
	Cache-Control
	Conenction
3. Representation Header 
	Content-Type
	Content-Length
	Content-Encoding
	ETag
4. Security Header
	Strict-Transport-Security (HSTS)
	Content-Security-Policy (CSP)
	X-Frame-Options
	X-Content-Type-Options
	Set-Cookie


Extensibility
Why Study Extensibility ?
Custom Header ?
Content-Negotitioan

Remote Control

---
HTTP Methods

GET
POST
PUT
PATCH
DELETE

Intent 
Semantic Meaning 

Idempotent vs Non-Idempotent

OPTIONS 
CORS 
Browser Have Same Origin Policy
Security Mechanism


CORS
1. Simple Flight Request
2. Pre-Flight Request
![[Sriniously-5-1.png]]

- How to disinguish b/w Simple and Pre-Flight Request ?
- Pre-Flight Request aka Cross Origin Request.

- Condition to satisfy to become Pre-Flight Request.

![[Sriniously-5-2.png]]
- Either One of them should be true.

- If a Content-Type : Appliction/JSON ? Which kind of Request it is ?


---
Content-Type 
1. General 
2. Other TODO  🤔🤔🤔 

Typical CORS Flow 
![[Sriniously-5-4.png]]


![[05. Understanding HTTP for backend engineers, where it all starts--31-48.png]] [[05. Understanding HTTP for backend engineers, where it all starts.mp4#t=1908|31:48]]

[[05. Understanding HTTP for backend engineers, where it all starts.mp4#t=2442|40:42]]

