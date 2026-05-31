# Module 08 — Specialized Data

> SQL isn't just rows and columns anymore. Documents, geometry, text search, and vectors all live
> in modern databases.

This is where the two engines show their personalities: PostgreSQL's `jsonb` and arrays vs SQL
Server's JSON functions; PostGIS vs `GEOGRAPHY`; `tsvector` vs full-text indexes; `pgvector` vs
SQL Server 2025 vectors.

## Contents

| # | Topic | One-liner |
|---|-------|-----------|
| 01 | [JSON](01.JSON.md) | 🟦 JSON functions vs 🐘 native `jsonb` |
| 02 | [XML](02.XML.md) | XML type, XQuery, FOR XML / shredding |
| 03 | [Spatial Data](03.Spatial-Data.md) | `GEOGRAPHY`/`GEOMETRY` vs PostGIS |
| 04 | [Arrays & Hierarchies](04.Arrays-and-Hierarchies.md) | 🐘 arrays + `ltree` vs 🟦 `HierarchyId` |
| 05 | [Full-Text Search](05.Full-Text-Search.md) | SQL Server FTS vs `tsvector`/`tsquery` |
| 06 | [Temporal & Vector Data](06.Temporal-and-Vector-Data.md) | System-versioned tables; vector search (SQL 2025 vs pgvector) |

## After this module you can

- Store and query JSON documents in either engine.
- Run geospatial and full-text queries.
- Use arrays/hierarchies and build AI vector search.

---
◀ Prev: [07 — Partitioning & Scale](../07-Partitioning-and-Scale/README.md) · ▲ [Course home](../README.md) · ▶ Next: [09 — Architecture & Internals](../09-Architecture-and-Internals/README.md)
