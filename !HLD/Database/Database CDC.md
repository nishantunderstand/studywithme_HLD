Database-ChangeTrack
CDC (Change Data Capture)
https://www.instagram.com/reel/DcQ1JtXpDdn/?utm_source=ig_web_copy_link&igsi=NTc4MTIwNjQ2YQ==

This website is really Good

- [ ] [[Database CDC Image.png]]
- [ ] [[Microservice Database CDC.excalidraw]]

---
If there is a change in DB 
How other service will now about it ?
CDC
Reason : DB Single Source of Truth


Continuous Montior Changes Publish Event to Kafka 
Kafka Send to Other System 

How CDC notice the changes ?
1. Short Polling | Not Suitable For Large System
2. DB Trigger | Slower Writes
3. Log Based | Low Latency  (MySQL / PostgreSQL)
Debezium (Read From Log)
Event to Kafka 
Kafka Fan Out Approach to Downstream System 