https://www.instagram.com/p/DfQ63U2j59f/


Database migrations: it works on your laptop, so why does production say the column does not exist? 👇  
  
You add a phone number to your sign-up page. On your laptop you add a phone column to the users table, and it works. You deploy, and production says: column "phone" does not exist. Why? There are 2 copies of the database, and you changed only yours.  
  
🔹 What a migration is  
A small file with 1 change to the structure of the database. You do not make the change by hand. You write it in a file, kept with your code:  
alter table users add column phone text;  
  
🔹 The files have an order  
Here they are numbered: file 1 created the users table, so this is file 2. Some tools use a timestamp or a chain of ids in place of 1, 2, 3.  
  
🔹 Each copy remembers  
With migrations, each copy of the database keeps a small table of the files it has already run. Your laptop: 1 and 2. Production: only 1.  
  
🔹 The migrate command  
A file changes nothing by itself. The migrate command compares the files in your code with that table. File 1 is already there, so it is skipped. File 2 is missing, so it runs, and 2 is written in the table. Now both copies have the same structure.  
  
🔹 Good to know  
Do not edit a file that has already run: the databases that ran it do not get your edit. Write a new file.  
Rails calls that table schema_migrations; Flyway calls it the schema history table.  
"Database migration" can also mean moving data from one system to another. This one is about the structure.

[[Day77_Database_Migration_OnPrem_To_AWS]]

https://www.instagram.com/p/DaxodtDT47r/


https://www.instagram.com/p/DfEbHbBDM3N/

----


https://www.instagram.com/p/DaqG1vcNaXD/

Zero-downtime database migration isn’t just about copying data. The real challenge is keeping the new database synchronized while users continue using the old one.  
  
A common production architecture looks like this:  
  
Source Database → Initial Snapshot → Debezium → Kafka → Consumer → Target Database  
  
1️⃣ Initial Snapshot  
The existing data (for example, 1 lakh rows) is copied from the source database to the target database to create a baseline.  
  
2️⃣ Debezium (CDC)  
While the snapshot is running, users continue creating, updating, and deleting data. Debezium continuously reads the database transaction log (PostgreSQL WAL, MySQL Binlog, MongoDB Oplog, etc.) and captures every INSERT, UPDATE, and DELETE event. This process is called Change Data Capture (CDC).  
  
3️⃣ Kafka  
Instead of writing directly to the target database, Debezium publishes these change events to Kafka. Kafka acts as a durable event stream, ensuring no changes are lost and allowing consumers to process events independently.  
  
4️⃣ Consumer  
A Kafka Consumer (or Kafka Connect Sink) reads these events and applies them to the target database.  
  
If both databases have the same schema (e.g., PostgreSQL → PostgreSQL), the consumer can directly apply the changes.  
  
If the schema is different (e.g., MongoDB → MySQL), the consumer first transforms the document into the target schema and then generates the appropriate SQL statements (INSERT, UPDATE, DELETE) before writing to the target database.  
  
The consumer keeps applying events until the replication lag becomes nearly zero. At that point, writes are paused for a few seconds, the final events are applied, and application traffic is switched to the new database.  
  
This is how production systems achieve near-zero downtime during database migrations.
