Types of Indexing 

Clustered vs Non-Clustered Indexing
- Primary Key is By Default Clustered index
- Clustered Index : physically sorts and stores table data on disk
- Only one Clustered Index is possible per table.
- Where is this Clustered Index Stored ?
- How many Clustered Index Table can have ?


- Non-Clustered Index
- B-Tree structure index value with pointers to actual row addresses
- Multiple Non-Clustered Indexes can exist on one table.

https://www.instagram.com/p/DYz4Y3ph4MH/




🧑‍💻 A Clustered Index physically sorts and stores table data on disk based on the indexed column. Only one Clustered Index is possible per table because physical ordering can only exist in one way — Primary Key automatically becomes Clustered in most databases. 

A Non-Clustered Index creates a separate B-Tree structure containing sorted indexed values with pointers to the actual row addresses — leaving physical table data untouched. Multiple Non-Clustered Indexes can exist on one table. 

Key trap — even with a Clustered Index, SELECT * does not guarantee sorted output without an explicit ORDER BY clause.


Does a Clustered Index guarantee that `SELECT * FROM Employee` will always return rows in sorted order based on the clustered index column, even without an explicit `ORDER BY` clause?