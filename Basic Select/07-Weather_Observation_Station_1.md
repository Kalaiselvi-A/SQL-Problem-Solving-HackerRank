## Problem: Weather Observation Station 1

### HackerRank Link
https://www.hackerrank.com/challenges/weather-observation-station-1/problem

---

### Problem Description
Retrieve a list of the `CITY` and `STATE` columns from the `STATION` table.

---

### Table Description
The `STATION` table contains weather station information, including:
- `CITY` — Name of the city where the station is located
- `STATE` — Name of the state where the station is located
- `LAT_N` — Northern latitude
- `LONG_W` — Western longitude

---

### SQL Query
```sql
SELECT CITY, STATE
FROM STATION;
```

---

### Explanation 
- `SELECT CITY, STATE` → Retrieves only the city and state columns
- `FROM STATION` → Specifies the table to query

---

### Key Learning
>_Selecting specific columns instead of all columns enhances clarity and efficiency when only certain data fields are required._

---
