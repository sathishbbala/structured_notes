## Access Exclusive Lock
An ACCESS EXCLUSIVE lock is the most restrictive lock mode in PostgreSQL. It conflicts with all other lock modes, meaning it completely blocks all concurrent reads (SELECT) and writes (INSERT, UPDATE, DELETE) on that table. Running operations that require this lock on a hot table (a heavily accessed production table) can instantly cause an application outage by backing up incoming queries and exhausting connection pools. The operations and commands that acquire an ACCESS EXCLUSIVE lock fall into three main categories:

# Data Definition Language (DDL) and Schema Alterations
Most schema modifications require an exclusive hold to prevent other transactions from interacting with an unstable table structure.
-   DROP TABLE: Completely removing a table.
-   ALTER TABLE ...: This includes almost all sub-commands, such as:
    - ADD COLUMN (Note: In modern Postgres, adding a column with a constant default is instant, but it still triggers a brief, transient ACCESS EXCLUSIVE lock)
    - DROP COLUMN
    - ALTER COLUMN TYPE (e.g., changing an int to a bigint)
    - RENAME (table or column names)
    - ADD/DROP CONSTRAINT
    - ENABLE/DISABLE TRIGGER or RULE
    - SET TABLESPACE
      
# Destructive Data Cleaning & Volume Operations
  Operations that bypass standard MVCC rows or aggressively manipulate underlying disk storage require full table isolation:
   - TRUNCATE: Fast, non-MVCC deletion of all table rows.
   - VACUUM FULL: Rebuilds the entire table on disk to reclaim space.(Standard VACUUM only takes a weaker SHARE UPDATE EXCLUSIVE lock, though it may briefly escalate to an ACCESS EXCLUSIVE lock at the very end to
       truncate empty pages at the tail of the file unless disabled via vacuum_truncate).

# Maintenance and Index Management
  - REINDEX: Rebuilding corrupted or bloated indexes (Unless run as REINDEX CONCURRENTLY).
  - CLUSTER: Physically reordering the table rows on disk based on an index.
  - REFRESH MATERIALIZED VIEW: Refreshing a materialized view (Unless the CONCURRENTLY option is provided, which downgrades the lock to EXCLUSIVE, allowing concurrent reads).

# Explicit Locking
  - LOCK TABLE <table_name> IN ACCESS EXCLUSIVE MODE;

# Comparison: Impact of DDL on Hot Tables
When migrating a hot table, understanding the duration of the ACCESS EXCLUSIVE lock is critical:

|Operation|Lock Taken|Danger Level on Hot Table|Why?|
|---------|----------|-------------------------|----|
|ADD COLUMN ... DEFAULT <constant>| ACCESS EXCLUSIVE| Low (Postgres 11+)| Fast metadata-only update; lock is held for milliseconds|
|ADD COLUMN ... NOT NULL (no default)| ACCESS EXCLUSIVE| High	| Requires a full table scan to verify that all existing rows satisfy the constraint|
|ALTER COLUMN TYPE| ACCESS EXCLUSIVE| Critical| Triggers a full table rewrite on disk, keeping the lock active for the duration of the data rewrite|
|CREATE INDEX| SHARE	|High	|Blocks writes (INSERT/UPDATE) during the build. Safe alternative: Use CREATE INDEX CONCURRENTLY|
