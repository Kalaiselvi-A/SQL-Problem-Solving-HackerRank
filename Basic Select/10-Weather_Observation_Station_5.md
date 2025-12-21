## Problem: Weather Observation Station 5

### HackerRank Link
https://www.hackerrank.com/challenges/weather-observation-station-5/problem

---

### Problem Description
Retrieve:
- The **city with the shortest name** and its length
- The **city with the longest name** and its length

If multiple cities have the same shortest or longest length, select the city that comes **first alphabetically**.

The results should be displayed as:
`CITY_NAME LENGTH`

---

### Table Description
The `STATION` table contains weather station information, including:
- `CITY` — Name of the city
- `STATE` — Name of the state
- `LAT_N` — Northern latitude
- `LONG_W` — Western longitude

---

### SQL Queries

```sql
#### Shortest City Name
SELECT CITY, LENGTH(CITY)
FROM STATION
ORDER BY LENGTH(CITY), CITY
LIMIT 1;

#### Longest City Name
SELECT CITY, LENGTH(CITY)
FROM STATION
ORDER BY LENGTH(CITY) DESC, CITY
LIMIT 1;

```

---

### Explanation 

#### Shortest city name query
- `LENGTH(CITY)` → Calculates number of characters
- `ORDER BY LENGTH(CITY), CITY`
  - First sorts by shortest length
  - Then alphabetically to handle ties
- `LIMIT 1` → Picks the first result

#### Longest city name query
- `ORDER BY LENGTH(CITY) DESC, CITY`
  - Sorts by longest length
  - Alphabetically for ties
- `LIMIT 1` → Picks the first result

---

### Key Learning
>_Using `ORDER BY` with multiple conditions allows precise control over sorting, while `LENGTH()` helps compare string sizes effectively._

---
