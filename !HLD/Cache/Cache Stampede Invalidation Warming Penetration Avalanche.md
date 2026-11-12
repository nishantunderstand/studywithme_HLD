
# Cache Invalidation vs Cache Stampede vs Cache Warming

- Cache Invalidation 
- Cache Stampede / Thundering Herd / Dogpile effect 
- Cache Warming

https://www.instagram.com/p/DaiNiicBhsj/


Hot / Popular Key 
1. One / Few Popular Key Expired : Cache Breakdown / Cache Stampde
2. Multiple Popular Key Expired Simuatlentously : Cache Avalanche

Solution :
- Request Coalescing / single-flight
- Distributed Lock
- Cache Warming
- Background Refresh
- Stale-While-Revalidate
- TTL Jitter


# Cache Stampede / Thundering Herd / Dogpile effect

Thundering Herd Problem
https://www.instagram.com/reels/Db8YSsrzb3q/


TTL 
Solution : 
1. Request Coaleasing (Single Request)
2. Cache Warming

https://www.instagram.com/p/DW9D_PWkfsJ/


# Cache Avalanche

Solution : 
1. TTL Jitter
2. Cache warming
3. Multiple cache layers
4. Circuit breaker
5. Rate limiting
6. Fallback

What is Cache Avalanche? How different From Cache Stampede ?


# Cache Penetration - Data does NOT exist
- Negative Caching
- Bloom Filter
- Input Validation
- Rate Limiting

Cache Penetration vs Cache Breakdown/Stampede vs Cache Avalanche




https://www.instagram.com/reel/Db3PQyGyJEI/
[[Redis Bloom Filter]]
