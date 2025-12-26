## Problem: Draw the Triangle 1

### HackerRank Link
https://www.hackerrank.com/challenges/draw-the-triangle-1/problem 

---

### Problem Summary
You need to generate a **triangle pattern** for `R` rows:

Example for `R = 5`:

  ```
  * * * * *
  * * * *
  * * *
  * *
  *
  ```

* Task: Write a query to print **P(20)**.
* Output format: Each row contains `*` separated by spaces.

---

### MySQL Query

```sql
WITH RECURSIVE numbers AS (
    SELECT 1 AS n
    UNION ALL
    SELECT n + 1 FROM numbers WHERE n < 20
)
SELECT REPEAT('* ', 21 - n) AS pattern
FROM numbers;
```

---

### Explanation

1. **Generate numbers 1 to 20**

```sql
WITH RECURSIVE numbers AS (
    SELECT 1 AS n
    UNION ALL
    SELECT n + 1 FROM numbers WHERE n < 20
)
```

* `numbers` CTE generates numbers from 1 to 20 representing **rows** of the triangle.

---

2. **Create the pattern per row**

```sql
SELECT REPEAT('* ', 21 - n) AS pattern
FROM numbers;
```

* `REPEAT('* ', 21 - n)` prints `* ` repeated `(21 - n)` times for each row.
* Row 1 → 20 stars, Row 2 → 19 stars … Row 20 → 1 star.

---

### Key Points

* Use **CTE with recursion** to generate a sequence of numbers in MySQL.
* `REPEAT` function efficiently prints repeated patterns.
* Adjust `REPEAT('* ', 21 - n)` depending on the number of rows (`R`) to match the pattern size.

---
