## Problem: Weather Observation Station 4

### HackerRank Link
https://www.hackerrank.com/challenges/weather-observation-station-4/problem

---

### Problem Description
Calculate the **difference** between:
- The **total number of CITY entries** in the `STATION` table, and
- The **number of distinct CITY entries** in the `STATION` table.

---

### Table Description
The `STATION` table contains weather station data with columns including:
- `ID`
- `CITY`
- `STATE`
- `LAT_N`
- `LONG_W`

---

### SQL Query
```sql
SELECT COUNT(CITY) - COUNT(DISTINCT CITY)
FROM STATION;
```

---

### Explanation 
- `COUNT(CITY)` → Counts all CITY entries (including duplicates)
- `COUNT(DISTINCT CITY)` → Counts only unique CITY names
- Subtracting them gives the **number of duplicate CITY entries**

---

### Key Learning
>_Using `COUNT()` and `COUNT(DISTINCT ...)` together allows you to determine the number of duplicate values in a column._

---
