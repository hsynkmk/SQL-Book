# Module 07 — Partitioning & Scale

> When one table gets huge, or one server isn't enough.

Partitioning splits a giant table into manageable pieces; columnstore turns it into an analytics
powerhouse; scaling out spreads load across machines. The concepts are shared; the syntax differs.

## Contents

| # | Topic | One-liner |
|---|-------|-----------|
| 01 | [Table Partitioning](01.Table-Partitioning.md) | Partition functions/schemes (🟦) vs declarative partitioning (🐘) |
| 02 | [Columnstore & Analytics Indexing](02.Columnstore-and-Analytics-Indexing.md) | Column-oriented storage for BI/OLAP |
| 03 | [Scaling Out](03.Scaling-Out.md) | Read replicas, sharding concepts, Citus / PolyBase |

## After this module you can

- Partition a large table by date and benefit from partition elimination.
- Use columnstore for analytic queries over millions of rows.
- Reason about read replicas and sharding for horizontal scale.

---
◀ Prev: [06 — Indexing & Performance](../06-Indexing-and-Performance/README.md) · ▲ [Course home](../README.md) · ▶ Next: [08 — Specialized Data](../08-Specialized-Data/README.md)
