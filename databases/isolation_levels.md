In a Relational Database, the transactions are a single logical unit of work. Transactions in a RDBMS must follow ACID properties. 

1. Atomicity - Atomicity is an all or nothing rule. Either all the changes made by a transaction are visible after a commit or none of the changes are visible following a rollback.
2. Consistency - Consistency is to ensure that the database remains in a consistent state before and after the transaction.
3. Isolation - Isolation means that the transactions execute in the database as if in isolation of other transactions.
4. Durability - All database changes that were committed are never lost. 

Before looking at the Isolation levels defined by the SQL standard, consider the following data anomalies that can cause data integrity issues with concurrent transactions. 
1. Dirty Read - This is a case when a transaction T1 has updated some value but has not committed yet. The transaction T2 reads the data that has not been committed yet. If the transaction T1 rolls back, the transaction T2 would have read data that did not exist. 
2. Repeatable Read - This is a case when a transaction T1 reads some data. Another transaction T2 later updates the value and commits the change. When the transaction T1 re-reads the data, the result is a different value.
3. Phantom Reads - Transaction T1 executes a query and gets a set of rows from the database. Transaction T2 inserts a new set of rows into the database. When the transaction T1 executes again, the transaction gets a different set of rows.

|Isolation level|Dirty Read|Repeatable Read|Phantom Read|
|---------------|----------|---------------|------------|
|Read uncommitted|:white_check_mark:|:white_check_mark:|:white_check_mark:|
|Read committed||:white_check_mark:|:white_check_mark:|
|Repeatable Read|||:white_check_mark:|
|Serializable|








