## Problem: Weather Observation Station 17

### HackerRank Link
https://www.hackerrank.com/challenges/weather-observation-station-17/problem

---

### Problem Description
From the `STATION` table:

- Find the **Western longitude (`LONG_W`)** of the row where the **smallest northern latitude (`LAT_N`)** is **greater than 38.7780**
- **Round the result** to **4 decimal places**

---

### Table Description
The `STATION` table contains the following fields:
- `LAT_N` — Northern latitude
- `LONG_W` — Western longitude
- Other station attributes

---

### SQL Query (MySQL → ORDER BY + LIMIT)

```sql
SELECT ROUND(LONG_W, 4)
FROM STATION
WHERE LAT_N > 38.7780
ORDER BY LAT_N
LIMIT 1;
```

---

### Explanation 
- `WHERE LAT_N > 38.7780` → Considers only northern latitudes **greater than 38.7780**.
- `ORDER BY LAT_N` → Brings the **smallest qualifying LAT_N** to the top.
- `LIMIT 1` → Returns the row with the **minimum LAT_N above the given value**.
- `ROUND(LONG_W, 4)` → Rounds the western longitude to **4 decimal places**.

---

### SQL Query (Alternative Approach - Subquery)

```sql
SELECT ROUND(LONG_W, 4)
FROM STATION
WHERE LAT_N = (
    SELECT MIN(LAT_N)
    FROM STATION
    WHERE LAT_N > 38.7780
);
```

---

### Explanation 
- **Subquery:**
    ```
    SELECT MIN(LAT_N)
    FROM STATION
    WHERE LAT_N > 38.7780
    ```
  - Finds the **smallest latitude** that is greater than `38.7780`.
- **outer query:**
    ```
    SELECT ROUND(LONG_W, 4)
    FROM STATION
    WHERE LAT_N = (…)
    ```
  - Selects the `LONG_W` value for the row where `LAT_N` matches the result of the subquery.
  - `ROUND(LONG_W, 4)` rounds the longitude to **4 decimal places**.
- This returns a **single numeric result** for the western longitude corresponding to the target latitude.

---

### Key Learning
>- _Using a subquery to identify a specific qualifying value (smallest above a threshold) allows you to then retrieve another attribute from the same row._
>- _`ROUND()` standardizes numeric precision in the final output._
>- _Sorting order (`ASC` vs `DESC`) decides whether you get a MIN or MAX value when using `LIMIT 1`._

---
