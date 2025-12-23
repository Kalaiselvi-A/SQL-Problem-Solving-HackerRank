## Problem: Weather Observation Station 19

### HackerRank Link
https://www.hackerrank.com/challenges/weather-observation-station-19/problem

---

### Problem Description
You are given a `STATION` table containing geographic coordinates.

Define two points on a 2D plane:
- **P1 (a, c)**
  - `a` = minimum value of `LAT_N`
  - `c` = minimum value of `LONG_W`
- **P2 (b, d)**
  - `b` = maximum value of `LAT_N`
  - `d` = maximum value of `LONG_W`

Your task is to:
- Calculate the **[Euclidean Distance](https://en.wikipedia.org/wiki/Euclidean_distance)** between points **P1** and **P2**
- Format the result to display **4 decimal places**

---

### [Euclidean Distance](https://en.wikipedia.org/wiki/Euclidean_distance) Formula
      Distance=√((b − a)² + (d − c)²)

---

### Table Description
The `STATION` table contains:
- `LAT_N` — Northern latitude
- `LONG_W` — Western longitude
- Other station attributes

---

### SQL Query (MySQL)

```sql
SELECT ROUND(
    SQRT(
        POWER(MAX(LAT_N) - MIN(LAT_N), 2) +
        POWER(MAX(LONG_W) - MIN(LONG_W), 2)
    ),
    4
)
FROM STATION;
```

---

### Explanation 
- `MIN(LAT_N), MAX(LAT_N), MIN(LONG_W), MAX(LONG_W)`
  - Identifies the smallest and largest latitude and longitude.
- **Apply Euclidean distance formula**
  ```
  SQRT(
    (MAX(LAT_N) - MIN(LAT_N))² +
    (MAX(LONG_W) - MIN(LONG_W))²
  )
  ```
  - Uses `POWER()` for squaring
  - Uses `SQRT()` to compute the square root
- ROUND(value, 4) → Displays the answer with **4 decimal places**, as required by HackerRank.

---

### Key Learning
>- _Euclidean distance measures straight-line distance using squared differences._
>- _SQL mathematical functions like `POWER()` and `SQRT()` allow complex calculations directly within queries._
>- _**Euclidean distance** in SQL can be calculated efficiently using aggregate functions with `POWER()` and `SQRT()` - no subqueries needed._

---​
