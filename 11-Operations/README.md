# Module 11 — Operations

> Keeping the database alive, fast, and recoverable. The DBA skill set — for both engines.

Backups you've tested, maintenance that prevents bloat, monitoring that catches problems early,
and automation that does it all while you sleep.

## Contents

| # | Topic | One-liner |
|---|-------|-----------|
| 01 | [Backup & Restore](01.Backup-and-Restore.md) | Full/diff/log + PITR (🟦) vs `pg_dump`/`pg_basebackup`/WAL PITR (🐘) |
| 02 | [Maintenance](02.Maintenance.md) | Index/stats upkeep vs `VACUUM`/`ANALYZE`/autovacuum tuning |
| 03 | [Monitoring & Diagnostics](03.Monitoring-and-Diagnostics.md) | DMVs/Query Store/Extended Events vs `pg_stat_*`/`pg_stat_statements` |
| 04 | [Automation](04.Automation.md) | SQL Server Agent vs `pg_cron` / external schedulers |
| 05 | [Capacity & Performance Counters](05.Capacity-and-Performance-Counters.md) | What to watch: cache hit, I/O, connections |

## After this module you can

- Design a backup strategy with point-in-time recovery — and test restores.
- Keep both engines healthy (defrag/stats vs vacuum/analyze).
- Find slow queries and blocking with the native tooling.
- Schedule maintenance jobs reliably.

---
◀ Prev: [10 — Security](../10-Security/README.md) · ▲ [Course home](../README.md) · ▶ Next: [12 — Data Warehousing, BI & Ecosystem](../12-DataWarehousing-BI-and-Ecosystem/README.md)
