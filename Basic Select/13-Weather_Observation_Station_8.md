## Problem: Weather Observation Station 8

### HackerRank Link
https://www.hackerrank.com/challenges/weather-observation-station-8/problem

---

### Problem Description
Retrieve a list of **distinct city names** from the `STATION` table where the city name **starts and ends with a vowel** (a, e, i, o, u).  
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
WHERE CITY REGEXP '^[AEIOUaeiou].*[AEIOUaeiou]$';
```

---

### Explanation 
- `SELECT DISTINCT CITY` → Retrieves **unique city names** (removes duplicates).
- `FROM STATION` → Specifies the source table (`STATION`).
- `WHERE CITY REGEXP '^[AEIOUaeiou].*[AEIOUaeiou]$'` → Filters city names that **start and end with a vowel**.
#### Regex breakdown:
- `^` → Start of the string
- `[AEIOUaeiou]` → First character must be a vowel
- `.*` → Allows any characters in between
- `[AEIOUaeiou]` → Last character must be a vowel
- `$` → End of the string

  Ensures **both first and last characters are vowels**.

---

### SQL Query (Alternative Approach - Without REGEXP)
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE LOWER(LEFT(CITY, 1)) IN ('a','e','i','o','u')
  AND LOWER(RIGHT(CITY, 1)) IN ('a','e','i','o','u');
```

---

### Explanation 
- `LEFT(CITY, 1)` extracts the first character
- `RIGHT(CITY, 1)` extracts the last character
- `LOWER()` handles case-insensitivity
- `IN (...)` checks for vowels

---

### Key Learning
>- _`^` and `$` are used to match **start and end** of strings_
>- _`REGEXP` (Regular Expression) - pattern-based string filtering_
>- _`LEFT()` and `RIGHT()` extract characters from strings_
>- _`DISTINCT` ensures no duplicate values in results_
>- _`LOWER()` ensures case-insensitive comparison_

---
