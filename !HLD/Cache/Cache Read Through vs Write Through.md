Cache Population Strategies
1. Cache-Aside (Lazy Loading)
2. Read-Through
3. Write-Through || Bank Balance 
4. Write-Behind


DB vs Cache 
- Which is updated first ?
- How to decide ?

- Banking Application / No Stale Data : Write Through
- Netflix / Instagram 


https://www.instagram.com/p/DacLvBEBkq-/

### Cache Strategy Comparison

![[Cache Starategy.png]]

|      Cache Aside       |      Read Through       |      Write Through      |
| :--------------------: | :---------------------: | :---------------------: |
| App manages Cache & DB | Cache manages DB Reads  | Cache manages DB Writes |
|      More Control      |      Cleaner Code       |   Better Consistency    |
|  Manual Cache Update   | Automatic Cache Loading |   Automatic DB Update   |
|      Most Common       |     Easy App Logic      | Keeps Cache & DB Synced |
|                        |     Cache Handle DB     | Writes go through Cache |
|                        |                         |   Banking Application   |
|                        |                         |      No Stale Data      |

Key Difference: 
The difference is NOT the architecture.
It is WHO manages the database interaction.


---



"Three caching patterns — each handles application, cache, and database differently.  
  
Cache Aside — application manages everything. On Cache Miss, application queries database and explicitly updates cache. Maximum control, more application complexity.  
  
Read Through — application only talks to cache. On Cache Miss, cache itself fetches from database, stores result, returns response. Application never touches database directly. Simplifies application logic.  
  
Write Through — every write goes through cache first. Cache synchronously updates database before confirming success. Cache and database always in sync — zero stale data risk. Slightly slower writes but strong consistency. Used for user profiles, bank balances, inventory — anywhere stale data is unacceptable.  
  
Cache Aside gives control. Read Through simplifies reads. Write Through ensures consistency."


