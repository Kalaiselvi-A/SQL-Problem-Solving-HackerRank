## Problem: Weather Observation Station 16

### HackerRank Link
https://www.hackerrank.com/challenges/weather-observation-station-16/problem

---

### Problem Description
From the `STATION` table:

- Find the **smallest northern latitude (`LAT_N`)** that is **greater than 38.7780**
- **Round** the result to **4 decimal places**

---

### Table Description
The `STATION` table contains:
- `LAT_N` — Northern latitude
- `LONG_W` — Western longitude
- Additional station attributes

---

### SQL Query (MySQL)

```sql
SELECT ROUND(MIN(LAT_N), 4)
FROM STATION
WHERE LAT_N > 38.7780;
```

---

### Explanation 
- `MIN(LAT_N)` finds the **smallest latitude value** greater than the given threshold.
- `WHERE LAT_N > 38.7780` filters only latitudes above 38.7780.
- `ROUND(value, 4)` rounds the result to **4 decimal places**.
- The query returns a **single numeric value**.

---

### Key Learning
> _Using `MIN()` with a `WHERE` clause retrieves the smallest value above a threshold, and `ROUND()` controls numeric precision for the result._

---
