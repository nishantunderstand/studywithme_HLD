[[Day21_Optimistic_vs_Pessimistic_Locking]]


Pessimistic Locking : Not Suitable for Distributed System

Optimistic Locking


https://www.instagram.com/p/DeZfXilB9xg/

Row Level Lock 


1 Product. 2 Buyers. Only 1 Stock Left! 😳😳  
  
What happens when two users try to buy the last available product at the same time?  
  
This is where database concurrency control becomes important.  
  
🔒 Pessimistic Locking: Lock the data before updating it. Other conflicting transactions must wait.  
  
⚡ Optimistic Locking: Don’t lock the row in advance. Check the version when updating. If the data has changed, reject the conflicting update.  
  
Both help prevent race conditions, but they work differently.  
  
Pessimistic = Lock first.  
Optimistic = Check before updating.  
  
Which one would you choose for a high-traffic application?


----

https://www.instagram.com/p/Den1au5qkpi/


Locking 
Shared Resource


---

https://www.instagram.com/p/DfQQ8SVoXzI/

1. Row Level Lock 
2. Version 
3. Hold
4. Unique Constraint 

----

https://www.instagram.com/p/DcT71HJyWCo/
