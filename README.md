# SQL — A Complete Course (SQL Server + PostgreSQL)

> **Read this repo top to bottom and you'll go from "what is a table?" to expert-level query
> optimization, internals, administration, and the BI/ETL ecosystem — fluent in both SQL Server
> and PostgreSQL.**

This isn't a reference dump — it's an **ordered curriculum**. The folders are numbered `00 → 13`.
Read them in order and each topic only relies on what came before. Every file starts with plain-
English intuition, shows the *painful before*, then the concept in portable SQL, then the **🟦 SQL
Server vs 🐘 PostgreSQL** differences side by side, and ends with **query challenges solved in
full**.

🎯 **In a hurry before an interview?** → [Interview Cheat Sheet](INTERVIEW_CHEATSHEET.md).
🛠️ **Set up first:** → [The Sample Database](SAMPLE-DATABASE.md) (every example runs against it).
🧭 **New to SQL?** → [What Is SQL & the Two Engines](00-Foundations/01.What-Is-SQL-and-the-Two-Engines.md).

## 🏷️ Dialect legend

| Badge | Means |
|-------|-------|
| 💻 **Standard SQL** | Portable ANSI form — works on most engines |
| 🟦 **SQL Server** | Microsoft SQL Server / T-SQL |
| 🐘 **PostgreSQL** | PostgreSQL |

When the engines agree, you'll see one block. When they diverge, you'll see them **side by side**.

---

## 🗺️ The Curriculum

| # | Module | What you'll learn |
|---|--------|-------------------|
| **00** | [Foundations](00-Foundations/README.md) | RDBMS & the two engines, relational model, ER design & normalization, data types, constraints |
| **01** | [Querying Basics](01-Querying-Basics/README.md) | SELECT/WHERE/ORDER BY, NULLs, joins, aggregation, subqueries, set ops, functions, pagination |
| **02** | [Advanced Querying](02-Advanced-Querying/README.md) | Window functions, CTEs & recursion, pivot/crosstab, CASE, grouping sets |
| **03** | [Modifying Data & DDL](03-Modifying-Data-and-DDL/README.md) | INSERT/UPDATE/DELETE, upsert/MERGE, schema DDL, identity/sequences, views, generated columns, temp tables |
| **04** | [Programmable SQL](04-Programmable-SQL/README.md) | Stored procedures, functions, triggers, error handling, dynamic SQL, cursors |
| **05** | [Transactions & Concurrency](05-Transactions-and-Concurrency/README.md) | ACID, isolation levels, locking/deadlocks, MVCC vs lock-based, optimistic/pessimistic |
| **06** | [Indexing & Performance](06-Indexing-and-Performance/README.md) | B-trees, clustered/heap, covering/filtered, execution plans, SARGability, statistics, maintenance, specialized indexes |
| **07** | [Partitioning & Scale](07-Partitioning-and-Scale/README.md) | Table partitioning, columnstore/analytics, scaling out |
| **08** | [Specialized Data](08-Specialized-Data/README.md) | JSON, XML, spatial, arrays/hierarchies, full-text search, temporal & vector data |
| **09** | [Architecture & Internals](09-Architecture-and-Internals/README.md) | SQL Server vs PostgreSQL architecture, storage/memory/WAL, the optimizer, HA & replication |
| **10** | [Security](10-Security/README.md) | Authentication, logins/users/roles, permissions, encryption, RLS/masking/auditing |
| **11** | [Operations](11-Operations/README.md) | Backup/restore & PITR, maintenance, monitoring/diagnostics, automation, capacity |
| **12** | [Data Warehousing, BI & Ecosystem](12-DataWarehousing-BI-and-Ecosystem/README.md) | DW design/SCD, SSIS, SSAS, SSRS, Power BI, PolyBase/FDW, dev tools, app integration |
| **13** | [Best Practices & Interview](13-Best-Practices-and-Interview/README.md) | Best practices, anti-patterns, study plan |

---

## 🧭 How to Study This

1. **Set up the [sample database](SAMPLE-DATABASE.md) first** — in SQL Server, PostgreSQL, or both.
   Then you can run every query you read.
2. **Don't skip Foundations.** The relational model and data types are the vocabulary for
   everything after.
3. **Feel the pain first.** Each file opens with a painful *before* — a wrong result, a slow query,
   a deadlock. The feature only makes sense against the problem it solves.
4. **Compare the dialects.** The 🟦/🐘 side-by-side sections are where "I know SQL" becomes "I know
   SQL Server *and* PostgreSQL."
5. **Do the 🎯 Practice.** Each topic ends with query challenges — attempt before peeking.
6. **Use the self-check questions** as your "ready to move on?" gate.

A week-by-week roadmap lives in the [Study Plan](13-Best-Practices-and-Interview/03.Study-Plan.md).

---

## 📐 How Each Topic Is Structured

Every file follows the same shape — intuition → the painful *before* → how it works → portable SQL
→ **🟦 SQL Server vs 🐘 PostgreSQL** → under-the-hood/performance → trade-offs → mistakes &
anti-patterns → real-world use → **practice with full solutions** → takeaways. See
[TEMPLATE.md](TEMPLATE.md).

> 💡 The golden rule of this repo: **SQL is a standard with two great dialects.** Learn the concept
> once, then the handful of places SQL Server and PostgreSQL diverge — and you're portable.

---

## 🤝 Contributing

PRs welcome. New content must follow [TEMPLATE.md](TEMPLATE.md) and run against the shared
[sample database](SAMPLE-DATABASE.md). Open an issue first for anything large.
