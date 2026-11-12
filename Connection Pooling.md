https://www.instagram.com/p/Dcodkjbh-WS/


Connection
Connection Proxy





Scaling your application is easy, you just add more servers. But what does that do to your database? 👇  
  
50 instances × 20 connections = 1000 connections asking for ~100 seats. Connection refused. Your traffic was never the problem, your fleet size was.  
  
❌ Raising the limit → connections aren’t free. The DB ends up managing connections instead of running queries.  
  
✅ Size the pool → 5 per instance, not 50. Total across the fleet must fit under the limit.  
  
✅ Connection proxy → 1000 patients, 20 doctors. Each query is short, so 20 real connections serve every instance. (PgBouncer, RDS Proxy)



---

https://www.instagram.com/p/DePcBLLTrgS/

PostgreSQL max 100
Connection Pool

General Rule : Connection Pool : Core * 2
