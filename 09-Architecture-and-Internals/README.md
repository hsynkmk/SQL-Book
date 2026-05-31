# Module 09 — Architecture & Internals

> Understand the engine and you stop being surprised by it.

Why does PostgreSQL need `VACUUM`? What is `tempdb` for? Where do query plans live? This module
opens the hood on both engines so the performance and operations modules make complete sense.

## Contents

| # | Topic | One-liner |
|---|-------|-----------|
| 01 | [SQL Server Architecture](01.SQL-Server-Architecture.md) | Protocol/relational/storage engine, buffer pool, tempdb, MDF/LDF |
| 02 | [PostgreSQL Architecture](02.PostgreSQL-Architecture.md) | Process model, shared_buffers, WAL, autovacuum |
| 03 | [Storage & Memory](03.Storage-and-Memory.md) | Pages, write-ahead logging, checkpoints, caching |
| 04 | [The Query Optimizer](04.The-Query-Optimizer.md) | Cost-based optimization, plan caching, prepared statements |
| 05 | [High Availability & Replication](05.High-Availability-and-Replication.md) | Always On vs streaming/logical replication, Patroni |

## After this module you can

- Describe how each engine processes a query end to end.
- Explain WAL, checkpoints, and (for PostgreSQL) MVCC bloat + autovacuum.
- Understand how plans are produced and cached.
- Compare the HA/DR options for each engine.

---
◀ Prev: [08 — Specialized Data](../08-Specialized-Data/README.md) · ▲ [Course home](../README.md) · ▶ Next: [10 — Security](../10-Security/README.md)
