## Problem: Draw the Triangle 2

### HackerRank Link
https://www.hackerrank.com/challenges/draw-the-triangle-2/problem

---

### Problem Summary

You are asked to generate a pattern `P(R)` of stars for `R` rows.  
For example, `P(5)` looks like:

  ```
  * 
  * * 
  * * * 
  * * * * 
  * * * * *
  ```

Each row `i` contains `i` stars.

---

### Task

Write a query to print **P(20)** — i.e., 20 rows of the pattern, where:

- Row 1 has `1` star
- Row 2 has `2` stars
- …
- Row 20 has `20` stars

---

### SQL Query (MySQL)

```sql
WITH RECURSIVE seq AS (
    SELECT 1 AS n
    UNION ALL
    SELECT n + 1 FROM seq WHERE n < 20
)
SELECT RTRIM(REPEAT('* ', n)) AS pattern
FROM seq;
```

---

### Explanation

1. **Generate Numbers 1 through 20**

```sql
WITH RECURSIVE seq AS (
    SELECT 1 AS n
    UNION ALL
    SELECT n + 1 FROM seq WHERE n < 20
)
```

* This recursive CTE generates a column `n` from 1 to 20, representing row numbers.

---

2. **Build the Star Pattern**

```sql
REPEAT('* ', n)
```

* Repeats the string `'* '` `n` times.
* For row 1: `'* '`
* Row 2: `'* * '`
* …
* Row 20: `'* * * ... * '` (20 stars)

---

3. **Remove Trailing Space**

```sql
RTRIM(...)
```

* Ensures output has no extra space at the end of each line.

---

### Key Points

>- _Recursive CTEs are useful for generating sequence tables without existing data._
>- _`REPEAT()` dynamically builds repeated patterns._
>- _`RTRIM()` cleans up trailing spaces in pattern output._

---
