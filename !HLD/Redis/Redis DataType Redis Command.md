What are Redis Data Types?
1. String
2. HashMap
3. List
4. Set
5. Ordered Set
6. Max Element that can be Stored

| Data Type       | Redis Name        | Common Commands                    | Typical Use                 |
| --------------- | ----------------- | ---------------------------------- | --------------------------- |
| **String**      | String            | `SET`, `GET`, `INCR`, `DECR`       | Cache, counters, tokens     |
| **Hash**        | Hash              | `HSET`, `HGET`, `HGETALL`          | Objects / key-value fields  |
| **List**        | List              | `LPUSH`, `RPUSH`, `LPOP`, `LRANGE` | Queues, recent items        |
| **Set**         | Set               | `SADD`, `SMEMBERS`, `SREM`         | Unique values               |
| **Sorted Set**  | Sorted Set / ZSet | `ZADD`, `ZRANGE`, `ZRANGEBYSCORE`  | Ranking, leaderboard        |
| **Stream**      | Stream            | `XADD`, `XREAD`, `XGROUP`          | Event streams               |
| **Bitmap**      | Bitmap            | `SETBIT`, `GETBIT`, `BITCOUNT`     | Compact boolean/state data  |
| **HyperLogLog** | HyperLogLog       | `PFADD`, `PFCOUNT`                 | Approximate unique-counting |
| **Geospatial**  | Geo               | `GEOADD`, `GEOSEARCH`              | Location/radius queries     |


- Max Element 2^32-1
- Is it case sensitive ?
- Does it support Atomic Operation ?



Redis Command : 

| Topic               | Command       |
| ------------------- | ------------- |
| Cache expiry        | EXPIRE / TTL  |
| Batch operation     | MSET / MGET   |
| Atomic counter      | INCR          |
| Distributed lock    | SET NX EX     |
| Queue               | LPUSH / RPUSH |
| Leaderboard         | ZADD          |
| Production scanning | SCAN          |
| Performance         | PIPELINE      |

