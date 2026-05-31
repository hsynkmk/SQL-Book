# Module 10 — Security

> The database holds your most sensitive data. Locking it down is non-negotiable.

Authentication, authorization, encryption, and row-level controls — both engines have rich
security models that map onto each other surprisingly well.

## Contents

| # | Topic | One-liner |
|---|-------|-----------|
| 01 | [Authentication](01.Authentication.md) | Windows/SQL auth (🟦) vs roles + `pg_hba.conf` (🐘) |
| 02 | [Logins, Users & Roles](02.Logins-Users-Roles.md) | Server vs database principals; role hierarchies |
| 03 | [Permissions](03.Permissions.md) | GRANT/REVOKE/DENY; schemas as a security boundary |
| 04 | [Encryption](04.Encryption.md) | TDE/Always Encrypted/column (🟦) vs pgcrypto/TLS/TDE distros (🐘) |
| 05 | [Row-Level Security, Masking & Auditing](05.Row-Level-Security-Masking-Auditing.md) | RLS (both!), dynamic data masking, audit trails |

## After this module you can

- Configure authentication and least-privilege roles in either engine.
- Grant exactly the access needed — no more.
- Encrypt data in transit and at rest.
- Enforce row-level security and audit access.

---
◀ Prev: [09 — Architecture & Internals](../09-Architecture-and-Internals/README.md) · ▲ [Course home](../README.md) · ▶ Next: [11 — Operations](../11-Operations/README.md)
