## Problem: Symmetric Pairs

### HackerRank Link
https://www.hackerrank.com/challenges/symmetric-pairs/problem

---

### Problem Description
You are given a table **Functions(X, Y)**.

Two rows `(X1, Y1)` and `(X2, Y2)` are **symmetric pairs** if:
- `X1 = Y2` **and**
- `X2 = Y1`

---

### Output Requirements
- Print all symmetric pairs
- Ensure `X ≤ Y`
- Order the result by `X` in ascending order

---

### SQL Query

```sql
SELECT f1.X, f1.Y
FROM Functions f1
JOIN Functions f2
  ON f1.X = f2.Y
 AND f1.Y = f2.X
WHERE f1.X <= f1.Y
GROUP BY f1.X, f1.Y
HAVING COUNT(*) > 1 OR f1.X < f1.Y
ORDER BY f1.X;
```

---

### Explanation 
- **Self-join:**
  - Finds pairs `(X1, Y1)` and `(X2, Y2)` such that `X1 = Y2` and `Y1 = X2` — i.e., **symmetric pairs**.
- **`WHERE f1.X <= f1.Y`:**
  - Avoids duplicate pairs `(1,2)` and `(2,1)`.
  - Ensures consistent ordering of output.
- **`GROUP BY f1.X, f1.Y`:**
  - Handles multiple identical rows in the table.
- **`HAVING COUNT(*) > 1 OR f1.X < f1.Y`:**
  - `COUNT(*) > 1`→ ensures `(X, X)` pairs are included if they appear twice.
  - `f1.X < f1.Y` → ensures `(X ≠ Y)` symmetric pairs are included only once.
- **`ORDER BY f1.X`:**
  - HackerRank requires sorting by `X`.
  
---

### Key Learning
>- _**Self-joins** are effective for finding symmetric relationships in a table._
>- _Always **handle duplicates and edge cases** carefully using `GROUP BY` and `HAVING` to ensure both `(X = Y)` and `(X ≠ Y)` pairs are included correctly._
>- _Use conditional filtering `(WHERE f1.X <= f1.Y)` and proper ordering `(ORDER BY)` to produce consistent, correct output in advanced join problems._

---
