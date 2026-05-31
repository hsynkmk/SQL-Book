# Module 02 — Advanced Querying

> Where SQL stops feeling like "fetch rows" and starts feeling like a query *language*.

Window functions, CTEs, and recursion are what separate intermediate SQL from expert SQL. The good
news: these are **highly standardized** — SQL Server and PostgreSQL agree on almost all of it.

## Contents

| # | Topic | One-liner |
|---|-------|-----------|
| 01 | [Window Functions](01.Window-Functions.md) | ROW_NUMBER/RANK/LAG/LEAD, running totals, frames |
| 02 | [CTEs & Recursion](02.CTEs-and-Recursion.md) | `WITH` clauses; recursive queries for trees/graphs |
| 03 | [Pivot & Crosstab](03.Pivot-and-Crosstab.md) | PIVOT/UNPIVOT (🟦) vs crosstab / FILTER (🐘) |
| 04 | [Conditional Logic](04.Conditional-Logic.md) | CASE, COALESCE, NULLIF |
| 05 | [Grouping Sets, ROLLUP, CUBE](05.Grouping-Sets-Rollup-Cube.md) | Multi-level subtotals in one query |

## After this module you can

- Rank, number, and compare rows with window functions.
- Write recursive CTEs to walk hierarchies (org charts, categories).
- Produce pivoted reports and multi-level subtotals.

---
◀ Prev: [01 — Querying Basics](../01-Querying-Basics/README.md) · ▲ [Course home](../README.md) · ▶ Next: [03 — Modifying Data & DDL](../03-Modifying-Data-and-DDL/README.md)
