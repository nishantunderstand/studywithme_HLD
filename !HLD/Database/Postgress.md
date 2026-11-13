
Auto Vaccum Cleaner 




https://www.instagram.com/p/Dd7eg-avt0Y/


Your Postgres table has 1M rows and is dragging 10M dead ones. That's why it's slow 👇  
  
1️⃣ An UPDATE never edits a row in place: it writes a new version, and the old one becomes a dead tuple  
2️⃣ Dead tuples stay in the table, so every scan reads through them  
3️⃣ VACUUM marks that space reusable, so new rows fill the holes instead of growing the table (the file doesn't shrink)  
4️⃣ Autovacuum waits until ~20% of a table is dead. On 100M rows, that's 20M dead rows before cleanup  
5️⃣ One long-running or idle-in-transaction session holds back cleanup for the whole database  
6️⃣ Fixes: lower autovacuum_vacuum_scale_factor on big tables, set idle_in_transaction_session_timeout, and watch n_dead_tup in pg_stat_user_tables  



---

Postgress Delete 100M Rows Postgress Got Slower



https://www.instagram.com/p/DeZSmqDjxel/


You delete 100 million old rows from a 500-million-row Postgres table. The command succeeds. Disk usage doesn't move — and your queries get slower.  
  
Here's why. A DELETE never removes the row. It stamps it dead and leaves it in the 8KB page, because an older transaction might still be allowed to see it. Every scan still walks those pages. Every index still points at them. Your cache fills with corpses.  
  
And autovacuum? By default it won't even start until one row in five is dead. On 500 million rows that's 100 million dead rows before cleanup begins. Even then, plain VACUUM only marks the space reusable inside the file — the docs are explicit that it does not return space to the operating system.  
  
The real answer is a schema decision, not a query: partition by the column you'll delete by, then DROP the partition. That's a file unlink. Instant, no dead tuples, disk returned.  
  
The rule: deleting by date → partition by date on day one. Scattered deletes → batch 10,000 at a time and drop autovacuum_vacuum_scale_factor to 0.01.

56 likes, 2 comments - codezup on October 12, 2026: "You delete 100 million old rows from a 500-million-row Postgres table. The command succeeds. Disk usage doesn't move — and your queries get slower.

Here's why. A DELETE never removes the row. It stamps it dead and leaves it in the 8KB page, because an older transaction might still be allowed to see it. Every scan still walks those pages. Every index still points at them. Your cache fills with corpses.

And autovacuum? By default it won't even start until one row in five is dead. On 500 million rows that's 100 million dead rows before cleanup begins. Even then, plain VACUUM only marks the space reusable inside the file — the docs are explicit that it does not return space to the operating system.

The real answer is a schema decision, not a query: partition by the column you'll delete by, then DROP the partition. That's a file unlink. Instant, no dead tuples, disk returned.

The rule: deleting by date → partition by date on day one. Scattered deletes → batch 10,000 at a time and drop autovacuum_vacuum_scale_factor to 0.01.

Follow @codezup for one system-design answer a day.
Comment GUIDE for the full write-up.

Comment "GUIDE" and I'll send you the full written breakdown.

#postgres #postgresql #database #vacuum #mvcc".