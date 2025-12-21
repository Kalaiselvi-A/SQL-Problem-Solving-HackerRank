## Problem: Weather Observation Station 3

### HackerRank Link
https://www.hackerrank.com/challenges/weather-observation-station-3/problem

---

### Problem Description
Retrieve a list of **city names** from the `STATION` table for cities that have an **even ID number**.  
The results should:
- Include only cities with an even `ID`
- Exclude duplicates
- Be returned in any order

---

### Table Description
The `STATION` table contains weather station information, including:
- `ID` — Unique identifier for the station
- `CITY` — Name of the city where the station is located
- `STATE` — State of the station
- `LAT_N` — Northern latitude
- `LONG_W` — Western longitude

---

### SQL Query
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE MOD(ID, 2) = 0;
```

---

### Explanation 
- `DISTINCT CITY` → removes duplicate city names
- `MOD(ID, 2) = 0` → selects rows where the ID is even
- `FROM STATION` → specifies the table

---

### Key Learning
>_Using `DISTINCT` removes duplicate values._
>_The `MOD` function can be used to filter numeric conditions such as even or odd identifiers._

---
