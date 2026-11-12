Cache Eviction Policies :
Cache needs space
Which entry should be removed?
1. LRU : Least Recently Used
2. LFU : Least Frequently Used
3. FIFO : First In First Out
4. TTL : Time To Live

**Expiration/TTL** → Entry becomes invalid after a certain time.


https://www.instagram.com/p/DblR--4S-kj/


That’s the job of cache eviction policies.  
  
Four you should know for system design interviews:  
  
FIFO: Evict the oldest entry  
LRU: Evict the least recently used  
LFU: Evict the least frequently used  
MRU: Evict the most recently used  
  
But don’t just memorize them.  
  
The real question is: what does your access pattern look like?  
  
FIFO: Simplicity and low overhead  
LRU: General purpose caching  
LFU: Stable, frequently accessed data  
MRU: One pass or sequential scans


https://bytebytego.com/guides/most-popular-cache-eviction/
