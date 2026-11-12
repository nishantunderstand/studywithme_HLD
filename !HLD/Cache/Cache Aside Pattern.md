Cache Population Strategies
1. Cache-Aside (Lazy Loading)
2. Read-Through
3. Write-Through
4. Write-Behind

Cache Aside Pattern												
- Pro 
- Cons
- Stale Data								

https://www.instagram.com/p/DaW1bKzB-OR/

Resturant Anlogy




Cache-Aside Race Conditions



Advnatages
- Database Load Reduced
- Faster Responses
- Only Frequent Used Data Cached
- Better Scalability

Disadvantages
- First Request is slow
- Cache can become stale
- Cache Invalidation Required



How to handle Cache Stale Issue 

[[Cache Read Through vs Write Through]]




"Cache Aside — also called Lazy Loading — is a caching strategy where the application checks cache first on every read request.  
  
Cache Hit — data found in cache, returned immediately from memory, database never touched.  
Cache Miss — data not in cache, application queries database, stores result in cache, returns response. Next request — Cache Hit.  
  
Cache only populates on demand — only truly accessed data lives in cache, no unnecessary memory usage.  
  
Advantages — reduced database load, faster repeated reads, resilient to cache failures since the app always falls back to database.  
  
Two challenges — first request penalty from the initial Cache Miss, and cache invalidation — if the database updates, cached copy becomes stale and must be explicitly invalidated.  
  
Instagram profiles, Netflix movie details, Amazon product pages all use this pattern."


---
https://www.instagram.com/engineerinazure/reel/Db0ltUYzfmS/
