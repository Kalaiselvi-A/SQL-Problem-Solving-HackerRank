## Problem: Weather Observation Station 20

### HackerRank Link
https://www.hackerrank.com/challenges/weather-observation-station-20/problem

---

### Problem Description
From the `STATION` table:

- Calculate the **median** of the Northern Latitudes (`LAT_N`)
- **Round** the result to **4 decimal places**

A **median** is the value separating the higher half of a dataset from the lower half.

---

### Table Description
The `STATION` table contains:
- `LAT_N` — Northern latitude
- `LONG_W` — Western longitude
- Other station-related fields

---

### SQL Query (MySQL Logic → Correct, HackerRank support → `Not supported`)

```sql
SELECT ROUND(AVG(LAT_N), 4)
FROM (
    SELECT LAT_N
    FROM STATION
    ORDER BY LAT_N
    LIMIT 2 - (SELECT COUNT(*) FROM STATION) % 2
    OFFSET (SELECT (COUNT(*) - 1) / 2 FROM STATION)
) AS median_table;
```

---

### Explanation 
- `ORDER BY LAT_N`
  - First, all latitude values are **sorted from smallest to largest.**
  - Imagine after sorting:
    ```
    Index (0-based):   LAT_N
      0                 10
      1                 20
      2                 30
      3                 40
      4                 50
      5                 60
    ```

- `OFFSET (COUNT(*) - 1) / 2`
  - This tells SQL **how many rows to SKIP**. (`OFFSET`)
  - **If total rows = 5 (ODD)**
      ```
      OFFSET = (5 - 1) / 2 = 2
      ```
      - Skip rows at index `0, 1` (first 2 rows skiped)
      - Start from index **2** (middle element)
  - **If total rows = 6 (EVEN)**
      ```
      OFFSET = (6 - 1) / 2 = 2
      ```
      - Skip rows at index `0, 1` (first 2 rows skiped)
      - Start from index **2** (first middle element)
    - Same `OFFSET` works for both cases.
- `LIMIT 2 - COUNT(*) % 2`
  - This tells SQL **how many rows to TAKE.**
      | Total rows | COUNT % 2 | LIMIT | Meaning              |
      | ---------- | --------- | ----- | -------------------- |
      | Odd (5)    | 1         | 1     | Take 1 middle value  |
      | Even (6)   | 0         | 2     | Take 2 middle values |
- **What rows are selected?**
  - ODD (5 rows) `LIMIT 1 OFFSET 2`
    - Picks: `30`
  - EVEN (6 rows) `LIMIT 2 OFFSET 2`
    - Picks:
      ```
                30
                40
      ```
- `AVG(LAT_N)`
  - Odd → AVG(30) = 30
  - Even → AVG(30, 40) = 35
- `ROUND(..., 4)`
  - Formats the median to **4 decimal places**.

---

### SQL Query (MySQL Logic → Correct, HACKERRANK-APPROVED SOLUTION)

```sql
SELECT ROUND(AVG(LAT_N), 4)
FROM (
    SELECT LAT_N,
           ROW_NUMBER() OVER (ORDER BY LAT_N) AS rn,
           COUNT(*) OVER () AS total
    FROM STATION
) t
WHERE rn IN (
    FLOOR((total + 1) / 2),
    CEIL((total + 1) / 2)
);
```

---

### Explanation 
- `ROW_NUMBER() OVER (ORDER BY LAT_N) AS rn`
  - Sorts all `LAT_N` values from **smallest to largest**
  - Assigns row numbers:
      | rn | LAT_N |
      | -- | ----- |
      | 1  | 12.34 |
      | 2  | 18.90 |
      | 3  | 25.67 |
      | 4  | 30.12 |
      | 5  | 40.55 |

- `COUNT(*) OVER () AS total`
  - Adds the **same total count value to every row**
  - Example: if there are 5 rows → `total = 5`
- **Identify the middle row(s)**
  ```
      FLOOR((total + 1) / 2)
      CEIL((total + 1) / 2)
  ```
  - Odd rows (5) `(total + 1) / 2 = 3`
    - Median row = **3**
  - Even rows (6) `(total + 1) / 2 = 3.5`
    - Median rows = **3 and 4**
- `WHERE rn IN (middle positions)`
  - Odd → selects **1 row**
  - Even → selects **2 rows**
- `AVG(LAT_N)`
  - 1 value → median = that value
  - 2 values → median = average
- `ROUND(..., 4)`
  - Rounds result to **4 decimal places** (as required)

> **Median in SQL = Sort → Number rows → Pick middle → Average**

---

### Key Learning
>- _Median calculation in SQL requires sorting and positional logic._
>- _Combining `ORDER BY`, `LIMIT`, `OFFSET`, and `AVG()` allows accurate median computation for both even and odd-sized datasets._
>- _**OFFSET = where to start, LIMIT = how many to take**_
>- _`OFFSET` tells SQL how many rows to SKIP before starting to return rows._

---
