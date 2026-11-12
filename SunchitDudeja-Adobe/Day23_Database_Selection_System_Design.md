# Day 23: Database Selection for System Design - The Architect's Complete Guide

## 🎯 The Interview Question That Exposes Your Experience

**Interviewer:** "You're designing a social media platform. How would you choose the right database(s)?"

**Junior's Answer:** "I'll use MySQL because I know it well."

**Architect's Answer:** "It depends on the data patterns. User profiles need ACID → PostgreSQL. Feed posts need flexible schema → MongoDB. Session data needs speed → Redis. Search needs full-text → Elasticsearch. The answer is polyglot persistence."

---

## 🧠 The 8 Key Factors Architects Consider

### Factor 1: Data Structure & Schema
```
┌─────────────────────────────────────────────────────────────┐
│                    DATA STRUCTURE                            │
├─────────────────────────────────────────────────────────────┤
│ Structured (Tables/Rows)     →  PostgreSQL, MySQL           │
│ Semi-Structured (JSON/XML)   →  MongoDB, CouchDB            │
│ Key-Value Pairs              →  Redis, DynamoDB             │
│ Wide-Column (Sparse Data)    →  Cassandra, HBase            │
│ Graph (Relationships)        →  Neo4j, Amazon Neptune       │
│ Time-Series                  →  InfluxDB, TimescaleDB       │
│ Blob/Files                   →  S3, Azure Blob, MinIO       │
└─────────────────────────────────────────────────────────────┘
```

### Factor 2: Read vs Write Patterns
```
Use Case                          | Recommended Database
----------------------------------|-------------------------
Read-Heavy (95% reads)            | Read Replicas + Redis Cache
Write-Heavy (IoT sensors)         | Cassandra, ScyllaDB
Balanced Read/Write               | PostgreSQL, MongoDB
Append-Only (Logs, Events)        | Kafka + Elasticsearch
Real-time Analytics               | ClickHouse, Druid
```

### Factor 3: Consistency Requirements (CAP Theorem)
```
┌─────────────────────────────────────────────────────────────┐
│                    CAP THEOREM                               │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│        Consistency (C)                                       │
│             /\                                               │
│            /  \                                              │
│           /    \                                             │
│    PostgreSQL   CockroachDB                                  │
│    MySQL        Spanner                                      │
│         /        \                                           │
│        /          \                                          │
│       /____________\                                         │
│  Availability(A)    Partition Tolerance(P)                   │
│      |                    |                                  │
│   Cassandra            MongoDB                               │
│   DynamoDB             Redis Cluster                         │
│                                                              │
│  CP: Strong consistency, may be unavailable during partition │
│  AP: Always available, eventually consistent                 │
│  CA: Not possible in distributed systems!                    │
└─────────────────────────────────────────────────────────────┘
```

### Factor 4: Scale Requirements
```
Vertical Scaling (Scale Up):
├── PostgreSQL (up to ~10TB, millions of rows)
├── MySQL (up to ~5TB with proper indexing)
└── Best for: Moderate scale, ACID requirements

Horizontal Scaling (Scale Out):
├── Cassandra (Petabyte scale, billions of rows)
├── MongoDB (Sharding across nodes)
├── DynamoDB (Unlimited with partitions)
└── Best for: Massive scale, write-heavy workloads

Global Distribution:
├── CockroachDB (Multi-region ACID)
├── Spanner (Google's global database)
├── Cosmos DB (Azure's global distribution)
└── Best for: Global apps, low latency worldwide
```

### Factor 5: Latency Requirements
```
┌─────────────────────────────────────────────────────────────┐
│                 LATENCY SPECTRUM                            │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  Microseconds (μs)          Milliseconds (ms)               │
│  ◄─────────────────────────────────────────────────────────►│
│                                                             │
│  Redis     DynamoDB    MongoDB    PostgreSQL    S3          │
│  (0.1ms)   (1-5ms)     (2-10ms)   (5-50ms)     (50-200ms)   │
│                                                             │
│  ⚡ Cache   ⚡ NoSQL     📄 Docs    🏛️ ACID     📦 Storage│
│                                                             │
└─────────────────────────────────────────────────────────────┘

Real-World Latency Targets:
- Gaming Leaderboard: < 1ms → Redis
- E-commerce Cart: < 10ms → DynamoDB/Redis
- Product Search: < 50ms → Elasticsearch
- Order History: < 200ms → PostgreSQL
- Video Files: < 500ms → S3 + CDN
```

### Factor 6: Transaction Requirements (ACID vs BASE)
```
ACID (Atomicity, Consistency, Isolation, Durability):
├── Use When: Financial transactions, inventory, bookings
├── Databases: PostgreSQL, MySQL, CockroachDB, Spanner
└── Example: Bank transfer must be atomic

BASE (Basically Available, Soft state, Eventually consistent):
├── Use When: Social feeds, analytics, caching
├── Databases: Cassandra, DynamoDB, MongoDB
└── Example: Like count can be eventually consistent
```

### Factor 7: Query Complexity
```
Simple Key Lookups:
├── Redis: GET user:123
├── DynamoDB: GetItem(PK="user#123")
└── Best for: Session data, caching

Complex Queries with JOINs:
├── PostgreSQL: SELECT * FROM orders JOIN users...
├── MySQL: Multi-table relationships
└── Best for: Reporting, analytics

Full-Text Search:
├── Elasticsearch: Match queries, fuzzy search
├── OpenSearch: Log analysis, search
└── Best for: Product search, log analysis

Graph Traversals:
├── Neo4j: MATCH (a)-[:FOLLOWS]->(b)
├── Neptune: Social network queries
└── Best for: Recommendations, fraud detection
```

### Factor 8: Operational Complexity & Cost
```
┌─────────────────────────────────────────────────────────────┐
│           OPERATIONAL COMPLEXITY MATRIX                      │
├─────────────────────────────────────────────────────────────┤
│ Database        │ Ops Complexity │ Cost Model     │ Managed │
├─────────────────┼────────────────┼────────────────┼─────────┤
│ PostgreSQL      │ Medium         │ Compute-based  │ RDS     │
│ MongoDB         │ Medium         │ Storage + Ops  │ Atlas   │
│ DynamoDB        │ Low            │ Request-based  │ Native  │
│ Cassandra       │ High           │ Node-based     │ Astra   │
│ Redis           │ Low            │ Memory-based   │ ElastiC │
│ Elasticsearch   │ High           │ Cluster-based  │ OpenS   │
│ CockroachDB     │ Medium         │ Node-based     │ Cloud   │
└─────────────────────────────────────────────────────────────┘
```

---

## 🏗️ Database Selection Decision Tree

```
START: What is your primary use case?
│
├─► Need ACID transactions?
│   ├─► Yes + Single Region → PostgreSQL/MySQL
│   └─► Yes + Multi-Region → CockroachDB/Spanner
│
├─► Flexible schema with documents?
│   ├─► Yes + ACID per document → MongoDB
│   └─► Yes + Simple key-value → DynamoDB
│
├─► Sub-millisecond latency needed?
│   ├─► Yes + Caching → Redis
│   └─► Yes + Persistence → Redis + AOF
│
├─► Massive write throughput?
│   ├─► Yes + Time-series → InfluxDB/TimescaleDB
│   └─► Yes + Wide-column → Cassandra/ScyllaDB
│
├─► Full-text search required?
│   └─► Yes → Elasticsearch/OpenSearch
│
├─► Complex relationships?
│   └─► Yes → Neo4j/Amazon Neptune
│
├─► Large file storage?
│   └─► Yes → S3/Azure Blob/GCS
│
└─► Analytics/OLAP workloads?
    └─► Yes → ClickHouse/Snowflake/BigQuery
```

---

## 📊 Real-World Architecture Examples

### Example 1: Amazon E-Commerce
```
┌─────────────────────────────────────────────────────────────┐
│                 AMAZON'S DATABASE ARCHITECTURE               │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  User Profiles    → PostgreSQL (ACID, structured)           │
│  Product Catalog  → DynamoDB (flexible schema, scale)       │
│  Shopping Cart    → Redis (speed, session)                  │
│  Order History    → DynamoDB (partition by user)            │
│  Payment Records  → PostgreSQL (ACID, compliance)           │
│  Product Search   → Elasticsearch (full-text)               │
│  Product Images   → S3 + CloudFront (blob storage + CDN)    │
│  Recommendations  → Neptune (graph relationships)           │
│  Analytics        → Redshift (OLAP, reporting)              │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

### Example 2: Netflix Streaming
```
┌─────────────────────────────────────────────────────────────┐
│                 NETFLIX'S DATABASE ARCHITECTURE              │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  User Accounts    → MySQL (billing, ACID)                   │
│  Viewing History  → Cassandra (massive writes, scale)       │
│  Recommendations  → Custom ML (graph-based)                 │
│  Session Data     → EVCache (Memcached, speed)              │
│  Video Metadata   → Cassandra (catalog, availability)       │
│  Video Files      → S3 (blob storage, CDN origin)           │
│  Search           → Elasticsearch (title search)            │
│  A/B Testing      → Cassandra (feature flags)               │
│  Analytics        → Druid + Spark (real-time analytics)     │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

### Example 3: Uber Ride-Sharing
```
┌─────────────────────────────────────────────────────────────┐
│                 UBER'S DATABASE ARCHITECTURE                 │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  User/Driver Data → PostgreSQL (ACID, structured)           │
│  Real-time Location→ Redis (speed, geo-queries)             │
│  Trip History     → Cassandra (scale, time-series)          │
│  Payments         → PostgreSQL (ACID, compliance)           │
│  Surge Pricing    → Redis (real-time calculations)          │
│  ETA Predictions  → Custom ML + Redis                       │
│  Geospatial Index → H3 + Redis (hexagonal indexing)         │
│  Analytics        → Hive + Presto (batch analytics)         │
│  Fraud Detection  → Graph DB + ML                           │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

---

## 🔴 Common Database Selection Mistakes

### Mistake 1: Using MongoDB for Transactions
```java
// ❌ WRONG: MongoDB for financial transactions
db.accounts.updateOne(
    { userId: "123" },
    { $inc: { balance: -100 } }
);
db.accounts.updateOne(
    { userId: "456" },
    { $inc: { balance: 100 } }
);
// What if second update fails? Money lost!

// ✅ RIGHT: Use PostgreSQL with transactions
BEGIN;
UPDATE accounts SET balance = balance - 100 WHERE user_id = '123';
UPDATE accounts SET balance = balance + 100 WHERE user_id = '456';
COMMIT;
// Atomic: Both succeed or both fail
```

### Mistake 2: Using SQL for Massive Write Throughput
```
// ❌ WRONG: PostgreSQL for IoT sensor data
// 1 million sensors sending data every second
// = 1 million INSERTs/second → PostgreSQL crashes

// ✅ RIGHT: Use Cassandra/TimescaleDB
// Cassandra handles millions of writes/second
// TimescaleDB optimized for time-series data
```

### Mistake 3: Using Cassandra for Complex Queries
```sql
-- ❌ WRONG: Cassandra doesn't support JOINs
SELECT * FROM orders 
JOIN users ON orders.user_id = users.id 
WHERE orders.date > '2024-01-01';
-- This query will FAIL in Cassandra

-- ✅ RIGHT: Denormalize data in Cassandra
-- Store user data with each order
-- Or use PostgreSQL for complex queries
```

### Mistake 4: Using Redis as Primary Database
```java
// ❌ WRONG: Redis for critical data without persistence
redis.set("user:123:balance", "5000");
// Server restarts → Data LOST!

// ✅ RIGHT: Redis as cache, PostgreSQL as source of truth
// Enable AOF persistence if Redis is critical
// Or use Redis for caching only
```

### Mistake 5: Using S3 for Small, Frequent Reads
```
// ❌ WRONG: S3 for user session data
// Latency: 50-200ms per read
// Cost: $$$ per million requests

// ✅ RIGHT: Use Redis/DynamoDB
// Latency: 0.1-5ms
// Optimized for small, frequent reads
```

---

## 📋 Database Selection Cheat Sheet

```
┌─────────────────────────────────────────────────────────────┐
│              DATABASE SELECTION CHEAT SHEET                  │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│ USE CASE                        │ DATABASE                  │
│ ────────────────────────────────┼─────────────────────────  │
│ User authentication & profiles  │ PostgreSQL                │
│ E-commerce orders & payments    │ PostgreSQL + Redis        │
│ Product catalog (flexible)      │ MongoDB / DynamoDB        │
│ Shopping cart & sessions        │ Redis                     │
│ Real-time leaderboards          │ Redis Sorted Sets         │
│ Social media feed               │ Cassandra + Redis         │
│ Chat messages                   │ Cassandra                 │
│ Full-text search                │ Elasticsearch             │
│ IoT sensor data                 │ TimescaleDB / InfluxDB    │
│ Video/Image storage             │ S3 + CloudFront           │
│ Social graph (friends/follows)  │ Neo4j                     │
│ Event sourcing                  │ Kafka + Cassandra         │
│ Global transactions             │ CockroachDB / Spanner     │
│ Analytics & reporting           │ ClickHouse / BigQuery     │
│ Feature flags                   │ Redis / LaunchDarkly      │
│ Rate limiting                   │ Redis                     │
│ Fraud detection                 │ Neo4j + ML                │
│ Log aggregation                 │ Elasticsearch             │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

---

## 🎯 Interview Questions & Answers

### Q1: "How would you choose between PostgreSQL and MongoDB?"

**Answer:**
```
PostgreSQL when:
- Complex relationships with JOINs
- ACID transactions required
- Data schema is well-defined
- Compliance requirements (banking, healthcare)

MongoDB when:
- Schema evolves frequently
- Document-oriented data (JSON)
- Horizontal scaling is priority
- Rapid prototyping needed
```

### Q2: "When would you use Cassandra over DynamoDB?"

**Answer:**
```
Cassandra when:
- Self-hosted/multi-cloud required
- More control over tuning
- Wide-column data model fits
- No vendor lock-in preferred

DynamoDB when:
- Fully managed preferred
- AWS ecosystem integration
- Predictable pricing model
- Serverless architecture
```

### Q3: "Why use multiple databases (Polyglot Persistence)?"

**Answer:**
```
Reasons:
1. Different data has different access patterns
2. No single DB excels at everything
3. Optimize cost and performance per use case
4. Scale different components independently

Example: Instagram
- User data → PostgreSQL (ACID)
- Posts/Feed → Cassandra (scale)
- Cache → Redis (speed)
- Search → Elasticsearch (full-text)
```

---

## 💡 Architect's Golden Rules

1. **Start with requirements, not technology** - Understand data patterns first
2. **Consider operational overhead** - Can your team manage it?
3. **Plan for scale, but don't over-engineer** - Start simple, evolve
4. **Polyglot persistence is normal** - Use the right tool for each job
5. **Always have a caching strategy** - Redis/Memcached for hot data
6. **Separate OLTP from OLAP** - Transactional vs analytical workloads
7. **Consider managed services** - RDS, Atlas, DynamoDB reduce ops burden
8. **Test with realistic data** - Performance varies with data size

---

## 🔗 Quick Reference Links

| Database | Best For | Avoid When |
|----------|----------|------------|
| **PostgreSQL** | ACID, complex queries | Massive writes |
| **MongoDB** | Flexible schema, docs | Complex JOINs |
| **Redis** | Caching, real-time | Primary storage |
| **Cassandra** | Write-heavy, scale | Complex queries |
| **DynamoDB** | Serverless, managed | Complex queries |
| **Elasticsearch** | Search, logs | Primary storage |
| **Neo4j** | Relationships | Simple key-value |
| **S3** | Large files | Small, frequent reads |
| **CockroachDB** | Global ACID | Simple single-region |

---

## 🎯 Key Takeaway

> **"The best database is the one that fits your use case, not the one that's trending on Twitter."**

An architect's job is to match data characteristics with database capabilities:
- **Structured + ACID** → Relational (PostgreSQL, MySQL)
- **Flexible + Scale** → Document (MongoDB, DynamoDB)
- **Speed + Caching** → In-Memory (Redis, Memcached)
- **Write-Heavy + Scale** → Wide-Column (Cassandra, ScyllaDB)
- **Relationships** → Graph (Neo4j, Neptune)
- **Search** → Search Engine (Elasticsearch)
- **Files** → Object Storage (S3, Azure Blob)

Master this, and you'll nail every system design interview! 🚀

---

*Next: Day 24 - Database Connection Pooling: How Booking.com handles holiday season traffic*

