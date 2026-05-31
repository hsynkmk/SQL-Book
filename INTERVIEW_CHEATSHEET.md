# SQL Interview Cheat Sheet (SQL Server 🟦 + PostgreSQL 🐘)

> One-page, high-yield reference for both engines. Legend: **🟦 = SQL Server / T-SQL**, **🐘 =
> PostgreSQL**, **💻 = standard SQL**. Each section links to its full chapter.

---

## 🔑 The dialect quick-reference (most-asked differences)

| Task | 🟦 SQL Server | 🐘 PostgreSQL |
|------|--------------|---------------|
| Limit rows | `SELECT TOP 10 …` / `OFFSET 10 ROWS FETCH NEXT 10 ONLY` | `LIMIT 10 OFFSET 10` |
| Auto key | `INT IDENTITY(1,1)` | `INT GENERATED ALWAYS AS IDENTITY` / `serial` |
| String concat | `+` or `CONCAT()` | `||` or `CONCAT()` |
| Null-coalesce | `ISNULL(x,y)` (2-arg) / `COALESCE` | `COALESCE(x,y)` |
| Current time | `GETDATE()` / `SYSDATETIME()` | `now()` / `CURRENT_TIMESTAMP` |
| String length | `LEN()` | `length()` (`char_length`) |
| Substring | `SUBSTRING`, `CHARINDEX`, `LEFT/RIGHT` | `substring`, `position`, `left/right` |
| Aggregate strings | `STRING_AGG(x, ',')` | `string_agg(x, ',')` |
| Cast | `CAST` / `CONVERT` / `TRY_CONVERT` | `CAST` / `x::type` |
| Upsert | `MERGE` | `INSERT … ON CONFLICT … DO UPDATE` |
| Get inserted id | `OUTPUT INSERTED.id` / `SCOPE_IDENTITY()` | `INSERT … RETURNING id` |
| Identifier quote | `[name]` | `"name"` (folds unquoted to lowercase) |
| Text type | `NVARCHAR(n)` / `NVARCHAR(MAX)` | `text` / `varchar(n)` |
| Boolean | `BIT` (0/1) | `boolean` (true/false) |
| Temp table | `#tmp` (session) / `##g` (global) | `CREATE TEMP TABLE` |
| Top-N per group | `ROW_NUMBER() OVER(PARTITION BY…)` | same (standard window fn) |
| Conditional | `IIF()` / `CASE` | `CASE` (no IIF) |
| Auto-increment seq | `SEQUENCE` (2012+) | `SEQUENCE` / `nextval()` |

---

## 📋 Query order of evaluation (write vs run)

```text
Written:  SELECT … FROM … JOIN … WHERE … GROUP BY … HAVING … ORDER BY … LIMIT/TOP
Logical:  FROM/JOIN → WHERE → GROUP BY → HAVING → SELECT → DISTINCT → ORDER BY → LIMIT
```
→ Why you **can't use a SELECT alias in WHERE** (WHERE runs before SELECT) but **can in ORDER BY**.

[Querying Basics →](01-Querying-Basics/01.SELECT-WHERE-ORDER-BY.md)

---

## 🔗 JOINs

```text
INNER  → rows matching in both          LEFT  → all left + matched right (NULLs if none)
RIGHT  → all right + matched left        FULL  → all rows, NULLs where unmatched
CROSS  → cartesian product               SELF  → table joined to itself (e.g. employee→manager)
Anti-join (rows with NO match): WHERE NOT EXISTS (SELECT 1 FROM b WHERE b.k=a.k)
```
[Joins →](01-Querying-Basics/03.Joins.md)

## ⚠️ NULL (three-valued logic)

```text
NULL = NULL → UNKNOWN (not true!).  Use IS NULL / IS NOT NULL.
x <> 'a' EXCLUDES rows where x IS NULL → add "OR x IS NULL".
COUNT(*) counts all rows; COUNT(col) skips NULLs. Most aggregates ignore NULL.
```
[NULL →](01-Querying-Basics/02.Working-with-NULL.md)

---

## 🪟 Window functions

```sql
ROW_NUMBER() OVER (PARTITION BY category ORDER BY price DESC)   -- 1,2,3 (unique)
RANK()       -- 1,2,2,4 (gaps)     DENSE_RANK() -- 1,2,2,3 (no gaps)
LAG(x)/LEAD(x) OVER (ORDER BY d)   -- previous/next row
SUM(x) OVER (ORDER BY d ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)  -- running total
```
Aggregate vs window: `GROUP BY` collapses rows; `OVER()` keeps every row + adds the calc.
[Window Functions →](02-Advanced-Querying/01.Window-Functions.md)

## 🔁 CTE & recursion

```sql
WITH RECURSIVE org AS (
  SELECT employee_id, manager_id, 1 AS lvl FROM employees WHERE manager_id IS NULL
  UNION ALL
  SELECT e.employee_id, e.manager_id, o.lvl+1 FROM employees e JOIN org o ON e.manager_id=o.employee_id
) SELECT * FROM org;     -- 🟦: omit the word RECURSIVE (WITH org AS …)
```
[CTEs →](02-Advanced-Querying/02.CTEs-and-Recursion.md)

---

## ✍️ Upsert (idempotent insert-or-update)

```sql
-- 🐘 PostgreSQL
INSERT INTO products (product_id, name, price) VALUES (1,'X',9.99)
ON CONFLICT (product_id) DO UPDATE SET name=EXCLUDED.name, price=EXCLUDED.price;

-- 🟦 SQL Server
MERGE products AS t USING (VALUES (1,'X',9.99)) AS s(id,name,price) ON t.product_id=s.id
WHEN MATCHED THEN UPDATE SET name=s.name, price=s.price
WHEN NOT MATCHED THEN INSERT (product_id,name,price) VALUES (s.id,s.name,s.price);
```
[Upsert/Merge →](03-Modifying-Data-and-DDL/02.Upsert-and-Merge.md)

---

## 🔒 Transactions, ACID & isolation

```text
ACID: Atomicity, Consistency, Isolation, Durability.
Isolation levels (weakest→strongest) and what they prevent:
  READ UNCOMMITTED  → dirty reads possible
  READ COMMITTED    → no dirty reads (🟦 default lock-based; 🐘 default MVCC)
  REPEATABLE READ   → no non-repeatable reads
  SERIALIZABLE      → no phantoms (fully isolated)
  SNAPSHOT (🟦)     → MVCC-style consistent snapshot
```
**MVCC (🐘 always; 🟦 with READ_COMMITTED_SNAPSHOT):** readers don't block writers (versions kept) — cost
is **VACUUM** to clear dead tuples. **Lock-based (🟦 default):** readers can block writers.
[ACID →](05-Transactions-and-Concurrency/01.Transactions-and-ACID.md) ·
[Isolation →](05-Transactions-and-Concurrency/02.Isolation-Levels.md) ·
[MVCC →](05-Transactions-and-Concurrency/04.MVCC-vs-Lock-Based.md)

**Optimistic vs pessimistic:** optimistic = version check at write (`WHERE version=@v`; 🟦 `ROWVERSION`,
🐘 `xmin`) for low contention; pessimistic = `SELECT … FOR UPDATE` (🐘) / `WITH (UPDLOCK)` (🟦) for hot
rows. Atomic `UPDATE … SET n=n-1 WHERE n>0` beats both for counters.
[Optimistic vs Pessimistic →](05-Transactions-and-Concurrency/05.Optimistic-vs-Pessimistic.md)

---

## ⚡ Indexing & performance (the big interview area)

```text
B-tree index → fast seeks on =, <, >, BETWEEN, prefix LIKE 'a%', ORDER BY.
Clustered (🟦) = table stored in index order (1 per table). Heap (🐘 default) = unordered + separate indexes.
Covering index = includes all columns a query needs → index-only scan (🟦 INCLUDE; 🐘 INCLUDE / index-only).
Filtered (🟦) / Partial (🐘) index = WHERE clause → smaller, for a subset.

SARGable = index-usable predicate. KILLERS:
  ❌ WHERE YEAR(d)=2025          ✅ d >= '2025-01-01' AND d < '2026-01-01'
  ❌ WHERE col*2 > 100           ✅ col > 50
  ❌ WHERE LIKE '%x%'            ✅ LIKE 'x%'  (or full-text/trigram for contains)
  ❌ implicit type conversion    ✅ match types

Read plans: 🟦 actual execution plan (SSMS) ·  🐘 EXPLAIN (ANALYZE, BUFFERS).
  Look for: Seek (good) vs Scan (often bad), estimated vs actual rows (stale stats), expensive sorts/spills.
```
[Indexing module →](06-Indexing-and-Performance/01.How-Indexes-Work.md) ·
[SARGability →](06-Indexing-and-Performance/05.SARGability.md) ·
[Plans →](06-Indexing-and-Performance/04.Reading-Execution-Plans.md)

**Specialized indexes:** 🟦 columnstore (analytics), full-text; 🐘 **GIN** (jsonb/arrays/FTS), **GiST**
(spatial/ranges), **BRIN** (huge ordered tables), hash.
[Specialized Indexes →](06-Indexing-and-Performance/08.Specialized-Indexes.md)

---

## 🧱 Normalization

```text
1NF: atomic values, no repeating groups.    2NF: 1NF + no partial dependency on part of a composite key.
3NF: 2NF + no transitive dependency (non-key → non-key).   BCNF: stricter 3NF.
Denormalize deliberately for read performance (warehouses) — trade integrity for speed.
```
[Normalization →](00-Foundations/03.ER-Design-and-Normalization.md)

---

## 🗄️ Architecture one-liners

```text
🟦 SQL Server: buffer pool (memory), tempdb (temp/version store/sorts), MDF/LDF files,
   transaction log (write-ahead), Always On Availability Groups (HA).
🐘 PostgreSQL: process-per-connection, shared_buffers, WAL (write-ahead log), autovacuum,
   streaming + logical replication, Patroni for HA. Each connection = a process → use PgBouncer.
Both: write-ahead logging (durability), cost-based optimizer + plan cache, checkpoints flush dirty pages.
```
[SQL Server Arch →](09-Architecture-and-Internals/01.SQL-Server-Architecture.md) ·
[PostgreSQL Arch →](09-Architecture-and-Internals/02.PostgreSQL-Architecture.md)

---

## 🛡️ Security & ops one-liners

```text
AuthZ: GRANT/REVOKE/DENY (🟦 has explicit DENY); roles bundle permissions; schemas as security boundary.
RLS (both): row-level security policies filter rows per user. Masking (🟦 dynamic data masking).
Backups: 🟦 full/differential/log + PITR via log restore · 🐘 pg_dump (logical) / pg_basebackup + WAL (PITR).
Monitoring: 🟦 DMVs / Query Store / Extended Events · 🐘 pg_stat_* / pg_stat_statements.
Automate: 🟦 SQL Server Agent · 🐘 pg_cron / external scheduler.
```
[Security →](10-Security/01.Authentication.md) · [Operations →](11-Operations/01.Backup-and-Restore.md)

---

## 📊 Data warehousing & BI

```text
Star schema: central FACT (measures + FK keys) + DIMENSION tables (descriptive). Snowflake = normalized dims.
SCD Type 1 (overwrite) · Type 2 (new row + validity dates, keeps history) · Type 3 (prev-value column).
ETL vs ELT: transform before load (SSIS) vs after (push compute into the warehouse — modern).
Power BI: Import (cached VertiPaq, fast, scheduled refresh) vs DirectQuery (live, index the source).
PG analogs: SSIS→COPY/FDW/dbt/Airflow · SSAS→materialized views/Cube.dev · SSRS→JasperReports.
```
[DW Design →](12-DataWarehousing-BI-and-Ecosystem/01.Data-Warehouse-Design.md)

---

## 🚫 Top anti-patterns (smell these instantly)

```text
SELECT *  ·  cursors/RBAR (use set-based)  ·  non-SARGable predicates  ·  implicit conversions
N+1 queries  ·  string-concatenated SQL (injection!)  ·  status<>'x' dropping NULLs
leading-wildcard LIKE '%x%'  ·  no ORDER BY but expecting order  ·  over/under-indexing
🟦 NOLOCK everywhere (dirty reads)  ·  🐘 huge OFFSET / autovacuum neglect / connection floods
```
[Anti-Patterns →](13-Best-Practices-and-Interview/02.Anti-Patterns.md)

---

## 💬 Classic interview questions (know the crisp answer)

1. **WHERE vs HAVING?** WHERE filters rows before grouping; HAVING filters groups after aggregation.
2. **DELETE vs TRUNCATE vs DROP?** DELETE = logged, row-by-row, WHERE-able; TRUNCATE = fast, resets,
   minimal log; DROP = removes the table.
3. **UNION vs UNION ALL?** UNION removes duplicates (sort/distinct cost); UNION ALL keeps all (faster).
4. **Clustered vs non-clustered index?** Clustered = the table's physical order (1); non-clustered =
   separate structure pointing back.
5. **Primary key vs unique?** PK = one per table, not null, identifies the row; UNIQUE = many allowed,
   permits one NULL (engine-dependent).
6. **Why is `SELECT *` bad?** Extra I/O, breaks on schema change, defeats covering indexes.
7. **What is a deadlock and how to handle?** Two txns each holding a lock the other needs; engine kills
   a victim → retry; prevent by consistent lock order + short transactions.
8. **MVCC vs locking?** MVCC keeps row versions so readers don't block writers (🐘 always; 🟦 snapshot)
   — cost is VACUUM; locking blocks (🟦 default).
9. **How to make a query SARGable?** Keep the indexed column bare (no function/expression), match types.
10. **CHAR vs VARCHAR vs NVARCHAR?** Fixed vs variable length; N = Unicode (🟦). 🐘: `text`/`varchar`.
11. **Stored procedure vs function?** Procs do actions/side effects (called with EXEC); functions
    return a value and are used inside queries (no side effects).
12. **How does an index speed up a query, and when does it hurt?** Speeds reads via seeks; hurts writes
    (must be maintained) and uses space — index for real patterns.

---

## 🧪 5-minute warm-up drills (sample DB)

```sql
-- 1. 2nd-highest price per category (top-N per group)
SELECT * FROM (SELECT *, ROW_NUMBER() OVER(PARTITION BY category_id ORDER BY unit_price DESC) rn
              FROM products) t WHERE rn = 2;
-- 2. Customers with no orders (anti-join)
SELECT c.* FROM customers c WHERE NOT EXISTS (SELECT 1 FROM orders o WHERE o.customer_id=c.customer_id);
-- 3. Running revenue total by date (window)
SELECT order_date, SUM(total) OVER(ORDER BY order_date) AS running FROM orders;
-- 4. Employee → manager chain (recursive CTE) — see CTE section above
-- 5. Idempotent upsert — see Upsert section above
```

[Full study plan & roadmap →](13-Best-Practices-and-Interview/03.Study-Plan.md) ·
[Course home →](README.md)
