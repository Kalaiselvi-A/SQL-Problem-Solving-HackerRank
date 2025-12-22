## Problem: Weather Observation Station 11

### HackerRank Link
https://www.hackerrank.com/challenges/weather-observation-station-11/problem

---

### Problem Description
Retrieve a list of **distinct city names** from the `STATION` table that **either**:
- Do **not start with a vowel** (a, e, i, o, u),  
**or**
- Do **not end with a vowel** (a, e, i, o, u)

The result must not contain duplicates.

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
WHERE CITY NOT REGEXP '^[AEIOUaeiou].*[AEIOUaeiou]$';
```

---

### Explanation 
- `^[AEIOUaeiou]` → CITY **starts with a vowel**
- `.*` → any number of characters in between
- `[AEIOUaeiou]$` → CITY **ends with a vowel**
- The full regex matches cities that **start AND end with vowels**
- `NOT REGEXP` → excludes those cities
    - So the result includes cities that:
      - do **not** start with a vowel **OR**
      - do **not** end with a vowel
- `DISTINCT` → removes duplicate city names

---

### SQL Query (Alternative Approach - Without REGEXP)
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE LOWER(LEFT(CITY,1)) NOT IN ('a','e','i','o','u')
   OR LOWER(RIGHT(CITY,1)) NOT IN ('a','e','i','o','u');
```

---

### Explanation 
- `LEFT(CITY, 1)` → gets the **first character**
- `RIGHT(CITY, 1)` → gets the **last character**
- `LOWER()` → handles case-insensitive comparison
- `NOT IN` ('a','e','i','o','u') → filters out vowels
- `OR` → selects cities that fail **either** condition
- `DISTINCT` → removes duplicate city names

---

### Key Learning
>- _`REGEXP` simplifies string pattern checks_
>- _`^` → start of string, `$` → end of string_
>- _Regex checks **start & end with vowels** in one condition_
>- _`NOT REGEXP` filters cities failing the condition_
>- _`DISTINCT` removes duplicates_

---
