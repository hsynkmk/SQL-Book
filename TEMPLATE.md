# Topic Template & Contributor Guide

Every topic file in this course follows the **same shape**. That consistency is what turns a pile
of notes into a *course*: once you've read two topics, you know exactly where to find the
intuition, the portable SQL, the dialect differences, or the practice in every other one.

## Dialect legend (used everywhere)

| Badge | Means |
|-------|-------|
| 💻 **Standard SQL** | Portable ANSI form — works on most engines |
| 🟦 **SQL Server** | Microsoft SQL Server / T-SQL specifics |
| 🐘 **PostgreSQL** | PostgreSQL specifics |

When the two engines agree, show one block. When they diverge, show them **side by side** (a
two-column table or paired 🟦/🐘 code blocks). Never make the reader guess which dialect a snippet
is.

---

## The Sections (in order)

1. **`# Title: <one-line intent>`** — the title names it; the subtitle is the one-line "what does
   this give me?".
2. **`## 🧠 Intuition`** — analogy / mental model. **No code.** If a smart beginner wouldn't follow
   it, simplify.
3. **`## 🎯 The Problem`** — a concrete scenario and the painful *before* (a wrong result, a slow
   query, unnormalized data, a deadlock). Make the reader feel the pain the feature relieves.
4. **`## 📐 How It Works`** — the concept. A diagram (Mermaid) or a worked example on the
   [sample database](SAMPLE-DATABASE.md) where it earns its keep.
5. **`## 💻 Standard SQL`** — the portable ANSI form, when one exists.
6. **`## 🟦 SQL Server vs 🐘 PostgreSQL`** — side-by-side syntax/behavior wherever they differ.
   For engine-only topics (architecture, SSRS), this becomes a comparison / "PostgreSQL analog"
   section.
7. **`## ⚡ Under the Hood / Performance`** — execution plan, index usage, cost. **Required** for
   query/performance topics; skip where it adds nothing.
8. **`## ⚖️ Trade-offs / When to Use`** — honest.
9. **`## 🚫 Common Mistakes & Anti-Patterns`** — `❌` wrong vs `✅` right.
10. **`## 🌍 Real-World Use`** — where this shows up in production systems.
11. **`## 🎯 Practice (with full solutions)`** — 2–4 query/scenario challenges against the
    [sample database](SAMPLE-DATABASE.md), each with a worked solution (both dialects where they
    diverge) and *why it works*.
12. **`## ✅ Key Takeaways`** — tight bullet summary, then **self-check questions**.
13. **Navigation footer** — `◀ Prev` · `▲ Module index` · `▶ Next` relative links.

---

## Conventions

- **Audience:** a developer who can write a little SQL but wants to go from beginner to expert, on
  **both** SQL Server and PostgreSQL.
- **All examples run against the shared [SAMPLE-DATABASE](SAMPLE-DATABASE.md)** so queries are
  consistent and copy-runnable.
- **Always label the dialect.** Use the badges; never leave a snippet ambiguous.
- **Cross-link liberally.** Relative links like `[Joins](01-Querying-Basics/03.Joins.md)` (add
  `../` across modules).
- **Diagrams:** Mermaid renders on GitHub. Keep them legible.
- **Tone:** direct, encouraging, no fluff. Short sentences. Goal is *understanding then applying*.
- **Show the "before."** The pain motivates the feature.
- **Verify dialect syntax against official docs** (Microsoft Learn for T-SQL; the PostgreSQL
  manual) — the engines diverge in subtle ways (`TOP` vs `LIMIT`, `GETDATE()` vs `now()`,
  `ISNULL` vs `COALESCE`, `IDENTITY` vs `GENERATED`, `MERGE` vs `ON CONFLICT`).

---

## Skeleton (copy me)

```markdown
# <Topic>: <one-line intent>

## 🧠 Intuition
<analogy / mental model — no code>

## 🎯 The Problem
<scenario + painful "before">

## 📐 How It Works
<concept, optional Mermaid / worked example on the sample DB>

## 💻 Standard SQL
\`\`\`sql
<portable form>
\`\`\`

## 🟦 SQL Server vs 🐘 PostgreSQL
| Concept | 🟦 SQL Server | 🐘 PostgreSQL |
|---------|--------------|---------------|
| ... | ... | ... |

## ⚡ Under the Hood / Performance
<execution plan / index usage>

## ⚖️ Trade-offs / When to Use

## 🚫 Common Mistakes & Anti-Patterns
<❌ / ✅>

## 🌍 Real-World Use

## 🎯 Practice (with full solutions)
### 1. <Challenge> — `Easy`
**Task:** ...
**Solution:**
\`\`\`sql
...
\`\`\`
**Why it works:** ...

## ✅ Key Takeaways
- ...

**Self-check:** <2–3 questions>

---
◀ [Prev](.) · ▲ [Module index](./README.md) · ▶ [Next](.)
```
