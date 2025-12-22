## Problem: Weather Observation Station 12

### HackerRank Link
https://www.hackerrank.com/challenges/weather-observation-station-12/problem

---

### Problem Description
Retrieve a list of **distinct city names** from the `STATION` table where the city name:
- **Does not start with a vowel** (a, e, i, o, u)
**and**
- **Does not end with a vowel** (a, e, i, o, u)

The result must **not contain duplicates**.

---

### Table Description
The `STATION` table contains weather station information, including:
- `ID`
- `CITY` — Name of the city
- `STATE`
- `LAT_N` — Northern latitude
- `LONG_W` — Western longitude

---

### SQL Query
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE CITY NOT REGEXP '^[AEIOUaeiou]'
  AND CITY NOT REGEXP '[AEIOUaeiou]$';
```

---

### Explanation 
- `^[AEIOUaeiou]` → cities starting with vowels
- `[AEIOUaeiou]$` → cities ending with vowels
- `NOT REGEXP` + `AND` → excludes both cases
- `DISTINCT` → removes duplicate city names

---

### Key Learning
> _Use `NOT REGEXP` **with start (`^`) and end (`$`) anchors** to efficiently filter strings that **neither start nor end with vowels** in a single, clean SQL condition._

---
