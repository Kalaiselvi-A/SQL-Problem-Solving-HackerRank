## Problem: Weather Observation Station 9

### HackerRank Link
https://www.hackerrank.com/challenges/weather-observation-station-9/problem

---

### Problem Description
Retrieve a list of **distinct city names** from the `STATION` table where the city name does **not start with a vowel** (i.e., does not begin with A, E, I, O, or U).  
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
WHERE CITY REGEXP '^[^AEIOUaeiou]';
```

---

### Explanation 
- `SELECT DISTINCT CITY` → Returns **unique city names** (removes duplicates).
- `FROM STATION` → Specifies the source table (`STATION`).
- `WHERE CITY REGEXP '^[^AEIOUaeiou]'` → Filters city names that **do NOT start with a vowel**.
#### Regexp breakdown:
- `^` → Start of the string
- `[^AEIOUaeiou]` → Matches any character **except vowels**

  This ensures the city name **starts with a consonant**.

---

### SQL Query (Alternative Approach - Without REGEXP)
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE LOWER(LEFT(CITY, 1)) NOT IN ('a','e','i','o','u');
```

---

### Explanation 
- `SELECT DISTINCT CITY` → Returns city names without duplicates.
- `LEFT(CITY, 1)` → Extracts the **first character** of each city name.
- `LOWER(...)` → Converts that character to lowercase to handle case-insensitive comparisons
    (e.g., A and a are treated the same).
- `NOT IN ('a','e','i','o','u')` → Filters out cities whose first letter is a vowel. Keeps only those cities that start with **consonants**.

---

### Key Learning
>- _`^` anchors the **start of a string**_
>- _`[^ ]` in regex means **NOT** (negation)_
>- _`REGEXP` is powerful for pattern matching_
>- _`DISTINCT` ensures no duplicate values in results_
>- _`NOT IN` is used to exclude specific values_
>- _`LEFT(column, n)` extracts characters from the beginning of a string_

---
