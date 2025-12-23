## Problem: Weather Observation Station 18

### HackerRank Link
https://www.hackerrank.com/challenges/weather-observation-station-18/problem

---

### Problem Description
You are given a `STATION` table containing geographic coordinates.

Define two points on a 2D plane:
- **P1 (a, b)**  
  - `a` = minimum value of `LAT_N`  
  - `b` = minimum value of `LONG_W`
- **P2 (c, d)**  
  - `c` = maximum value of `LAT_N`  
  - `d` = maximum value of `LONG_W`

Your task is to:
- Compute the **[Manhattan Distance](https://xlinux.nist.gov/dads/HTML/manhattanDistance.html)** between P1 and P2
- Round the result to **4 decimal places**

---

### [Manhattan Distance](https://xlinux.nist.gov/dads/HTML/manhattanDistance.html) Formula
    Manhattan Distance=∣a−c∣+∣b−d∣

---

### Table Description
The `STATION` table includes:
- `LAT_N` — Northern latitude
- `LONG_W` — Western longitude
- Other station-related fields

---

### SQL Query (MySQL)

```sql
SELECT ROUND(
    ABS(MIN(LAT_N) - MAX(LAT_N)) +
    ABS(MIN(LONG_W) - MAX(LONG_W)),
    4
)
FROM STATION;
```

---

### Explanation 
- `MIN(LAT_N), MAX(LAT_N), MIN(LONG_W), MAX(LONG_W)`
  - Finds the minimum and maximum latitude and longitude values.
- **Apply Manhattan distance formula**
  ```
  ABS(MIN(LAT_N) - MAX(LAT_N)) 
  + 
  ABS(MIN(LONG_W) - MAX(LONG_W))
  ```
  - Uses `ABS()` to ensure **positive** distances.
- ROUND(value, 4) → Rounds the final distance to **4 decimal places**, as required.

---

### Key Learning
>- _Aggregate functions like `MIN()` and `MAX()` can be combined with mathematical operations to compute distances._
>- _The Manhattan distance relies on absolute differences rather than geometric distance._
>- _**Manhattan Distance** in SQL can be computed directly using `MIN()`, `MAX()`, `ABS()`, and arithmetic - no subqueries required._

---
