# Module 00 — Foundations

> The vocabulary and mental model for everything after. Don't skip this.

Before you can query well, you need to know what a table *is*, how to design one, what types its
columns hold, and what rules (constraints) keep the data honest — in both SQL Server and
PostgreSQL.

## Contents

| # | Topic | One-liner |
|---|-------|-----------|
| 01 | [What Is SQL & the Two Engines](01.What-Is-SQL-and-the-Two-Engines.md) | RDBMS, SQL the language, SQL Server vs PostgreSQL, installing both |
| 02 | [The Relational Model](02.Relational-Model.md) | Tables, rows, columns, schemas, keys |
| 03 | [ER Design & Normalization](03.ER-Design-and-Normalization.md) | Entity-relationship design, 1NF/2NF/3NF/BCNF, when to denormalize |
| 04 | [Data Types](04.Data-Types.md) | Numeric/char/date/binary — 🟦 vs 🐘 side by side |
| 05 | [Constraints & Keys](05.Constraints-and-Keys.md) | PK/FK/UNIQUE/CHECK/NOT NULL/DEFAULT |

## After this module you can

- Explain what an RDBMS is and how SQL Server and PostgreSQL relate.
- Design a normalized schema and know when to denormalize.
- Pick the right column type in either engine.
- Enforce data integrity with constraints.

> 🛠️ Set up the [sample database](../SAMPLE-DATABASE.md) before starting.

---
▲ [Course home](../README.md) · ▶ Next module: [01 — Querying Basics](../01-Querying-Basics/README.md)
