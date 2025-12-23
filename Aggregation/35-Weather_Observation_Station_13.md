## Problem: Weather Observation Station 13

### HackerRank Link
https://www.hackerrank.com/challenges/weather-observation-station-13/problem

---

### Problem Description
Calculate the **sum of northern latitudes (`LAT_N`)** in the `STATION` table for rows where:

- `LAT_N` is **greater than 38.7880**
- `LAT_N` is **less than 137.2345**

Truncate the result to **4 decimal places**.

---

### Table Description
The `STATION` table contains weather station data including:
- `LAT_N` — Northern latitude
- `LONG_W` — Western longitude
- Other station attributes

---

### SQL Query (MySQL)
```sql
SELECT TRUNCATE(SUM(LAT_N), 4)
FROM STATION
WHERE LAT_N > 38.7880
  AND LAT_N < 137.2345;
```

---

### Explanation 
- `SUM(LAT_N)` computes the total of all northern latitude values meeting the conditions.
- `WHERE LAT_N > 38.7880 AND LAT_N < 137.2345` filters the latitudes within the given range.
- `TRUNCATE(value, 4)` cuts the result after 4 decimal places **without rounding**.
- Important: `TRUNCATE` ≠ `ROUND`
- The output is a **single numeric result**.

---

### Key Learning
>- _Use `TRUNCATE()` when the problem explicitly says **truncate**, not round._
>- _`SUM()` aggregates numeric values._
>- _`TRUNCATE()` controls decimal precision without rounding._
>- _Combining conditional filters with aggregation produces targeted summaries._

---
