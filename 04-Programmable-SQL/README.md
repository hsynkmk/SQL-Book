# Module 04 — Programmable SQL

> SQL has a procedural side. This is where T-SQL and PL/pgSQL go their separate ways.

Stored procedures, functions, and triggers let you put logic *in* the database. The two engines
share the concepts but have **very different procedural languages** — this module shows both.

## Contents

| # | Topic | One-liner |
|---|-------|-----------|
| 01 | [Stored Procedures](01.Stored-Procedures.md) | T-SQL procs vs PL/pgSQL procedures |
| 02 | [Functions](02.Functions.md) | Scalar + table-valued (TVF vs set-returning functions) |
| 03 | [Triggers](03.Triggers.md) | AFTER/INSTEAD OF (🟦) vs BEFORE/AFTER row/statement (🐘) |
| 04 | [Error Handling](04.Error-Handling.md) | TRY/CATCH + THROW vs EXCEPTION blocks |
| 05 | [Dynamic SQL & Control Flow](05.Dynamic-SQL-and-Control-Flow.md) | `sp_executesql` vs `EXECUTE`; variables, loops, IF |
| 06 | [Cursors & Why to Avoid Them](06.Cursors-and-Why-to-Avoid-Them.md) | Row-by-row processing and its set-based alternative |

## After this module you can

- Write stored procedures and functions in both T-SQL and PL/pgSQL.
- Use triggers for auditing/enforcement (and know their costs).
- Handle errors and avoid the cursor trap.

---
◀ Prev: [03 — Modifying Data & DDL](../03-Modifying-Data-and-DDL/README.md) · ▲ [Course home](../README.md) · ▶ Next: [05 — Transactions & Concurrency](../05-Transactions-and-Concurrency/README.md)
