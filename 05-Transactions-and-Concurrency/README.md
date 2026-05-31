# Module 05 — Transactions & Concurrency

> What keeps your data correct when many users hit it at once. The deepest conceptual difference
> between the two engines lives here.

Transactions give you ACID guarantees. Isolation levels and concurrency control decide how the
database behaves under contention — and **SQL Server (lock-based + optional snapshot)** and
**PostgreSQL (MVCC by default)** take genuinely different paths.

## Contents

| # | Topic | One-liner |
|---|-------|-----------|
| 01 | [Transactions & ACID](01.Transactions-and-ACID.md) | BEGIN/COMMIT/ROLLBACK; the four guarantees |
| 02 | [Isolation Levels](02.Isolation-Levels.md) | Read phenomena; the standard levels + snapshot |
| 03 | [Locking, Blocking, Deadlocks](03.Locking-Blocking-Deadlocks.md) | How contention happens and how to resolve it |
| 04 | [MVCC vs Lock-Based](04.MVCC-vs-Lock-Based.md) | 🐘 MVCC + vacuum vs 🟦 locks + row-versioning |
| 05 | [Optimistic vs Pessimistic](05.Optimistic-vs-Pessimistic.md) | rowversion / xmin, `SELECT ... FOR UPDATE` |

## After this module you can

- Reason about what a transaction guarantees and when it rolls back.
- Choose an isolation level deliberately, knowing the phenomena it allows.
- Explain why PostgreSQL readers don't block writers, and what `VACUUM` is for.
- Pick optimistic vs pessimistic concurrency for a given workload.

---
◀ Prev: [04 — Programmable SQL](../04-Programmable-SQL/README.md) · ▲ [Course home](../README.md) · ▶ Next: [06 — Indexing & Performance](../06-Indexing-and-Performance/README.md)
