# Module 12 — Data Warehousing, BI & Ecosystem

> From transactional databases to analytics, reporting, and the tools around them.

This module covers data-warehouse design (engine-neutral) and the **Microsoft BI/ETL stack**
(SSIS, SSAS, SSRS, Power BI) — with **PostgreSQL analogs** noted throughout, since PostgreSQL has
no first-party equivalents to those products.

## Contents

| # | Topic | One-liner |
|---|-------|-----------|
| 01 | [Data Warehouse Design](01.Data-Warehouse-Design.md) | Star/snowflake, fact/dimension, SCD, conformed dimensions |
| 02 | [ETL with SSIS](02.ETL-with-SSIS.md) | SSIS packages; 🐘 analogs: `COPY`, FDW, external ETL (Airflow/dbt) |
| 03 | [OLAP with SSAS](03.OLAP-with-SSAS.md) | Multidimensional & tabular, MDX/DAX; 🐘 analog notes |
| 04 | [Reporting with SSRS](04.Reporting-with-SSRS.md) | Paginated reports; 🐘 reporting options |
| 05 | [Power BI Integration](05.Power-BI-Integration.md) | DirectQuery/Import against both engines |
| 06 | [PolyBase, FDW & Big Data](06.PolyBase-FDW-and-Big-Data.md) | Querying external data: PolyBase vs foreign data wrappers |
| 07 | [Dev Tools](07.Dev-Tools.md) | SSMS/ADS/SSDT/sqlcmd/bcp vs psql/pgAdmin/pg_dump |
| 08 | [Application Integration](08.Application-Integration.md) | ADO.NET/EF Core, pyodbc/psycopg, JDBC, Node; DevOps/CI-CD |

## After this module you can

- Design a star-schema warehouse and handle slowly changing dimensions.
- Understand the Microsoft BI stack and its PostgreSQL alternatives.
- Connect applications and BI tools to either engine.
- Set up database DevOps and CI/CD.

---
◀ Prev: [11 — Operations](../11-Operations/README.md) · ▲ [Course home](../README.md) · ▶ Next: [13 — Best Practices & Interview](../13-Best-Practices-and-Interview/README.md)
