## Problem: Weather Observation Station 2

### HackerRank Link
https://www.hackerrank.com/challenges/weather-observation-station-2/problem

---

### Problem Description
You are given a `STATION` table containing geographic data.

You need to:
1. Calculate the **sum of all LAT_N values**
2. Calculate the **sum of all LONG_W values**
3. **Round both results to 2 decimal places**
4. Display the output in a single row as:
    `lat lon`

---

### Table Description
The `STATION` table contains:
- `LAT_N` → Northern latitude
- `LONG_W` → Western longitude

---

### SQL Query (MySQL)
```sql
SELECT 
    ROUND(SUM(LAT_N), 2),
    ROUND(SUM(LONG_W), 2)
FROM STATION;
```

---

### Explanation 
- `SUM(LAT_N)` → Calculates the total of all latitude values
- `SUM(LONG_W)` → Calculates the total of all longitude values
- `ROUND(value, 2)` → Rounds the result to **2 decimal places**
- No `GROUP BY` is required because we want a **single aggregated result**

---

### Key Learning
>- _Aggregate functions like `SUM()` return a single value._
>- _`ROUND()` controls decimal precision in SQL outputs._
>- _Multiple aggregate results can be returned in one `SELECT` statement._

---
