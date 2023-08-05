In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), **ACID** ([atomicity](https://en.wikipedia.org/wiki/Atomicity_(database_systems) "Atomicity (database systems)"), [consistency](https://en.wikipedia.org/wiki/Consistency_(database_systems) "Consistency (database systems)"), [isolation](https://en.wikipedia.org/wiki/Isolation_(database_systems) "Isolation (database systems)"), [durability](https://en.wikipedia.org/wiki/Durability_(database_systems) "Durability (database systems)")) is a set of properties of [database transactions](https://en.wikipedia.org/wiki/Database_transaction "Database transaction") intended to guarantee data validity despite errors, power failures, and other mishaps.
ACID transactions guarantee that a database will be in a consistent state after running a group of operations.
A transaction is a group of database read and write operations that only succeeds if all the operations within succeed. Transactions can impact a single record or multiple records.


### Atomicity

Atomicity guarantees that all of the commands that make up a transaction are treated as a single unit and either succeed or fail together. This is important as in the case of an unwanted event

### Consistency

Consistency guarantees that changes made within a transaction are consistent with database constraints. This includes all rules, constraints, and triggers. If the data gets into an illegal state, the whole transaction fails.

### Isolation

Isolation ensures that all transactions run in an isolated environment. That enables running transactions concurrently because transactions don’t interfere with each other.

### Durability

Durability guarantees that once the transaction completes and changes are written to the database, they are persisted. This ensures that data within the system will persist even in the case of system failures like crashes or power outages.

###
**Atomicity**: Money needs to both be removed from one account and added to the other, or the transaction will be aborted. Removing money from one account without adding it to another would leave the data in an inconsistent state.
**Consistency**: Consider a database constraint that an account balance cannot drop below zero dollars. All updates to an account balance inside of a transaction must leave the account with a valid, non-negative balance, or the transaction should be aborted.
**Isolation**: Consider two concurrent requests to transfer money from the same bank account. The final result of running the transfer requests concurrently should be the same as running the transfer requests sequentially.
**Durability**: Consider a power failure immediately after a database has confirmed that money has been transferred from one bank account to another. The database should still hold the updated information even though there was an unexpected failure.