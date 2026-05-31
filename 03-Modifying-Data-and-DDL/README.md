# Module 03 — Modifying Data & DDL

> Writing data and shaping the schema. The dialects diverge a lot here — upsert and identity
> especially.

You've queried; now you'll insert, update, delete, and design. This module covers DML writes, the
upsert problem (where 🟦 and 🐘 differ most), schema DDL, and views.

## Contents

| # | Topic | One-liner |
|---|-------|-----------|
| 01 | [INSERT, UPDATE, DELETE](01.Insert-Update-Delete.md) | The write trio + `OUTPUT`/`RETURNING` |
| 02 | [Upsert & MERGE](02.Upsert-and-Merge.md) | `MERGE` vs `INSERT ... ON CONFLICT` |
| 03 | [Creating & Altering Schema](03.Creating-and-Altering-Schema.md) | CREATE/ALTER/DROP databases, tables, schemas |
| 04 | [Identity & Sequences](04.Identity-and-Sequences.md) | IDENTITY vs GENERATED / SERIAL / sequences |
| 05 | [Views & Materialized Views](05.Views-and-Materialized-Views.md) | Virtual tables; indexed views (🟦) vs materialized views (🐘) |
| 06 | [Computed & Generated Columns](06.Computed-and-Generated-Columns.md) | Columns derived from other columns |
| 07 | [Temporary Tables & Table Variables](07.Temporary-Tables-and-Table-Variables.md) | Scratch space: `#temp`, table variables, `TEMP` tables |

## After this module you can

- Modify data safely and return what changed (`OUTPUT`/`RETURNING`).
- Implement upsert correctly in both engines.
- Design and evolve schemas, views, and generated columns.

---
◀ Prev: [02 — Advanced Querying](../02-Advanced-Querying/README.md) · ▲ [Course home](../README.md) · ▶ Next: [04 — Programmable SQL](../04-Programmable-SQL/README.md)
