# Databases

## What problem do databases solve?

Applications need to retain information beyond a single program execution and allow multiple users or services to read and change it safely. A database provides structured storage and mechanisms for querying, updating, protecting, and recovering data.

## Why were they created?

Ad hoc files become difficult to query, update consistently, share concurrently, and recover after failures. Database systems evolved to manage these concerns behind defined data models and interfaces.

## How to study a database concept

Start with a concrete workload. What data is stored? Which queries must be fast? What happens when two users update the same record? What if the process or machine crashes halfway through a transaction?

## Topics

- Relational model, tables, keys, constraints
- SQL and query execution
- Indexes: B-trees and hash indexes
- Transactions and ACID
- Isolation levels, locks, and MVCC
- Query planning and optimization
- WAL, checkpoints, backup, and recovery
- Replication, partitioning, and sharding
- NoSQL data models and trade-offs
- Caching and connection pooling

**Labs:** use PostgreSQL. Design a schema, inspect query plans with `EXPLAIN ANALYZE`, add an index, run concurrent transactions, and observe what changes.