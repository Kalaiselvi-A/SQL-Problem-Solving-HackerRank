## Problem: Weather Observation Station 15

### HackerRank Link
https://www.hackerrank.com/challenges/weather-observation-station-15/problem

---

### Problem Description
From the `STATION` table:

- Find the **Western longitude (`LONG_W`)** for the row that has the **largest northern latitude (`LAT_N`)**  
- But only consider latitudes **less than 137.2345**
- **Round the result to 4 decimal places**

---

### Table Description
The `STATION` table contains:
- `LAT_N` — Northern latitude
- `LONG_W` — Western longitude
- Additional station attributes

---

### SQL Query (MySQL → ORDER BY + LIMIT)

```sql
SELECT ROUND(LONG_W, 4)
FROM STATION
WHERE LAT_N < 137.2345
ORDER BY LAT_N DESC
LIMIT 1;
```

---

### Explanation 
- `WHERE LAT_N < 137.2345` → Only considers northern latitudes strictly less than 137.2345.
- `ORDER BY LAT_N DESC` → Brings the **largest LAT_N** to the top.
- `LIMIT 1` → Returns the **single row** with the largest LAT_N under the limit.
- `ROUND(LONG_W, 4)` → Ensures the output is formatted to **4 decimal places**.

---

### SQL Query (Alternative Approach - Subquery)

```sql
SELECT ROUND(LONG_W, 4)
FROM STATION
WHERE LAT_N = (
    SELECT MAX(LAT_N)
    FROM STATION
    WHERE LAT_N < 137.2345
);
```

---

### Explanation 
- **The inner query:**
    ```
    SELECT MAX(LAT_N)
    FROM STATION
    WHERE LAT_N < 137.2345
    ```
  - Finds the **largest latitude** that is less than `137.2345`.
- **The outer query:**
    ```
    SELECT ROUND(LONG_W, 4)
    FROM STATION
    WHERE LAT_N = (…)
    ```
  - Finds the `LONG_W` for that latitude.
  - `ROUND(LONG_W, 4)` rounds the longitude to **4 decimal places**.
- No `GROUP BY` is needed because the subquery returns a **single matching row**.

---

### Key Learning
>- _Using a subquery to find a specific row (e.g., the row with the largest qualifying value) allows you to then retrieve a related column from that row._
>- _Aggregates like `MAX()` can be combined with precise rounding functions._
>- _**When you need a value associated with the maximum or minimum of another column under a condition, use `ORDER BY … DESC/ASC` with `LIMIT 1`.**_

---
