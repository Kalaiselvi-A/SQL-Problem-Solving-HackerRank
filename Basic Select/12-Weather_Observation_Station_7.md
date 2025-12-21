## Problem: Weather Observation Station 7

### HackerRank Link
https://www.hackerrank.com/challenges/weather-observation-station-7/problem

---

### Problem Description
Retrieve a list of **distinct city names** from the `STATION` table where the city name **ends with a vowel** (a, e, i, o, or u).  
Your result must **not contain duplicates**.

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
WHERE CITY REGEXP '[AEIOUaeiou]$';
```

---

### Explanation 
- `SELECT DISTINCT CITY` → Retrieves **unique city names** (removes duplicates).
- `FROM STATION` → Specifies the source table (`STATION`).
- `CITY REGEXP '^[AEIOUaeiou]'` → Filters city names that **end with a vowel**.
#### Regex breakdown:
- `[AEIOUaeiou]` → Matches any vowel (uppercase or lowercase)
- `$` → Ensures the match occurs at the end of the string

  This guarantees that only cities **ending with a vowel** are selected.

---

### SQL Query (Alternative Approach - Using RIGHT() + LOWER())
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE LOWER(RIGHT(CITY, 1)) IN ('a','e','i','o','u');
```

---

### Explanation 
- `RIGHT(CITY, 1)` extracts the last character
- `LOWER()` handles case-insensitivity
- `IN (...)` checks for vowels

---

### Key Learning
>- _`$` in regex matches the end of a string_
>- _`REGEXP` is powerful for pattern-based string filtering_
>- _`RIGHT()` extracts characters from the end of a string._
>- _`DISTINCT` ensures no duplicate values in results_
>- _Multiple SQL solutions can be **equally correct**_

---
