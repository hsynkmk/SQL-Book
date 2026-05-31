# Module 06 — Indexing & Performance

> The module that turns "my query is slow" into "here's the index it needed, and here's the proof."

Indexes are the single biggest lever on query performance. This module covers how they work, how
to read execution plans in both engines, and how to write queries the optimizer can actually
accelerate.

## Contents

| # | Topic | One-liner |
|---|-------|-----------|
| 01 | [How Indexes Work](01.How-Indexes-Work.md) | B-tree fundamentals |
| 02 | [Clustered, Nonclustered & Heaps](02.Clustered-Nonclustered-Heaps.md) | 🟦 clustered index vs 🐘 heap + indexes |
| 03 | [Covering, Filtered & Included](03.Covering-Filtered-Included.md) | INCLUDE columns vs partial indexes |
| 04 | [Reading Execution Plans](04.Reading-Execution-Plans.md) | SSMS plans vs `EXPLAIN (ANALYZE, BUFFERS)` |
| 05 | [SARGability](05.SARGability.md) | Writing index-friendly predicates |
| 06 | [Statistics & Cardinality](06.Statistics-and-Cardinality.md) | How the optimizer estimates rows |
| 07 | [Index Maintenance](07.Index-Maintenance.md) | Rebuild/reorg vs REINDEX/VACUUM; bloat |
| 08 | [Specialized Indexes](08.Specialized-Indexes.md) | Columnstore vs GIN/GiST/BRIN/hash; full-text |

## After this module you can

- Read an execution plan and spot a scan that should be a seek.
- Design covering/filtered indexes for hot queries.
- Write SARGable predicates and keep statistics healthy.
- Choose the right specialized index for the data shape.

---
◀ Prev: [05 — Transactions & Concurrency](../05-Transactions-and-Concurrency/README.md) · ▲ [Course home](../README.md) · ▶ Next: [07 — Partitioning & Scale](../07-Partitioning-and-Scale/README.md)
