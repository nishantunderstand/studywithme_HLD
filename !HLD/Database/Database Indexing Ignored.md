
https://www.instagram.com/p/Da71th_vEXV/

View this post on Instagram A post shared by backendMorphism (@backendmorphism)

Q: Why do databases sometimes ignore an index?  
  
What Actually Happens?  
Having an index doesn't guarantee the database will use it.  
  
The query optimizer always chooses the execution plan with the lowest estimated cost. .  
  
Why Does This Happen?  
1️⃣ Too Many Rows Match:  
If a query returns a large percentage of the table, scanning the entire table can be faster than using an index.  
.  
2️⃣ Outdated Statistics:  
The optimizer relies on table statistics. If they're stale, it may choose a less efficient execution plan.  
.  
3️⃣ Low-Selectivity Columns:  
Indexes on columns with very few unique values (like status = 'ACTIVE') often provide little benefit.  
.  
4️⃣ Functions on Indexed Columns:  
Using functions like UPPER(name) or YEAR(order_date) can prevent the database from using the index unless a matching functional index exists.  
  
----  
  
Production Rule:  
An index improves performance only when it helps the optimizer find a cheaper execution plan.  
  
---  
  
Interview One-Liner:  
Databases may ignore an index when a full table scan is estimated to be faster based on factors like data distribution, stale statistics, low selectivity, or query expressions.
