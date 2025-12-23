## Problem: Weather Observation Station 14

### HackerRank Link
https://www.hackerrank.com/challenges/weather-observation-station-14/problem

---

### Problem Description
Find the **greatest value of the northern latitude (`LAT_N`)** in the `STATION` table that is **less than 137.2345**, and **truncate** the result to **4 decimal places**.

---

### Table Description
The `STATION` table contains weather station data including:
- `LAT_N` — Northern latitude
- `LONG_W` — Western longitude
- Other station columns

---

### SQL Query (MySQL)
```sql
SELECT TRUNCATE(MAX(LAT_N), 4)
FROM STATION
WHERE LAT_N < 137.2345;
```

---

### Explanation 
- `MAX(LAT_N)` finds the **highest latitude** among rows satisfying the condition.
- `WHERE LAT_N < 137.2345` ensures only values below the given threshold are considered.
- `TRUNCATE(value, 4)` truncates (not rounds) the result to **4 decimal places**.
- The output is a **single numeric value**.

---

### Key Learning
>- _Using `MAX()` with `WHERE` lets you find the largest value under a condition._
>- _`TRUNCATE()` provides precise control over decimal precision without rounding._

---
