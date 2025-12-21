## Problem: Weather Observation Station 6

### HackerRank Link
https://www.hackerrank.com/challenges/weather-observation-station-6/problem

---

### Problem Description
Retrieve a list of **distinct city names** from the `STATION` table where the city name **starts with a vowel** (a, e, i, o, u).  
The result should not contain duplicate city names.

---

### Table Description
The `STATION` table contains weather station information, including:
- `ID` 
- `CITY` — Name of the city
- `STATE` — Name of the state
- `LAT_N` — Northern latitude
- `LONG_W` — Western longitude

---

### SQL Query
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE CITY REGEXP '^[AEIOUaeiou]';
```

---

### Explanation 
- `SELECT DISTINCT CITY` → Retrieves **unique city names** (removes duplicates).
- `FROM STATION` → Specifies the source table.
- `CITY REGEXP '^[AEIOUaeiou]'` → Filters cities that **start with a vowel**.
#### Regex breakdown:
- `^` → Start of the string
- `[AEIOUaeiou]` → Matches any vowel (uppercase or lowercase)

---

### SQL Query (Alternative Approach - Using LEFT() + LOWER())
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE LOWER(LEFT(CITY, 1)) IN ('a','e','i','o','u');
```

---

### Explanation 
- `LEFT(CITY, 1)` → Extracts the **first character** of the city name.
- `LOWER(...)` → Converts it to lowercase to avoid case issues.
- `IN ('a','e','i','o','u')` → Checks whether the first letter is a vowel.
- `DISTINCT` → Removes duplicate city names.

---

### Key Learning
>- _`DISTINCT` is used to remove duplicate records._
>- _`REGEXP` helps in advanced pattern matching._
>- _`LEFT()` and `SUBSTRING()` extract parts of a string._
>- _`LOWER()` ensures case-insensitive comparisons._
>- _There are **multiple valid ways** to solve the same SQL problem._

---
