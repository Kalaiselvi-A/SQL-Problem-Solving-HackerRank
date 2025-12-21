## Problem: Weather Observation Station 10

### HackerRank Link
https://www.hackerrank.com/challenges/weather-observation-station-10/problem

---

### Problem Description
Retrieve a list of **distinct city names** from the `STATION` table where the city name **does not end with a vowel** (i.e., it ends with any character that is not a, e, i, o, or u).  
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
WHERE CITY REGEXP '[^AEIOUaeiou]$';
```

---

### Explanation 
- `SELECT DISTINCT CITY` → Returns **unique city names** (removes duplicates).
- `FROM STATION` → Specifies the source table (`STATION`).
- `WHERE CITY REGEXP '[^AEIOUaeiou]$'` → FFilters city names that **do NOT end with a vowel**.
#### Regexp breakdown:
- `[^AEIOUaeiou]` → Matches any character **except vowels**
- `$` → Ensures the match occurs at the **end of the string**

  This guarantees the city name **ends with a consonant**.

---

### SQL Query (Alternative Approach - Without REGEXP)
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE LOWER(RIGHT(CITY, 1)) NOT IN ('a','e','i','o','u');
```

---

### Explanation 
- `SELECT DISTINCT CITY` → Returns city names without duplicates.
- `RIGHT(CITY, 1)` → Extracts the **last character** of each city name.
- `LOWER(...)` → Converts that character to lowercase to handle case-insensitive comparisons
    (e.g., `A` and `a` are treated the same).
- `NOT IN ('a','e','i','o','u')` → Filters out cities whose last letter is a vowel. Keeps only those cities that end with **consonants**.

---

### Key Learning
>- _`$` anchors the **end of a string**_
>- _`[^ ]` in regex means **NOT** (negation)_
>- _`REGEXP` is powerful for pattern matching_
>- _`DISTINCT` ensures no duplicate values in results_
>- _`NOT IN` is used to exclude specific values_
>- _`Right(column, n)` extracts characters from the end of a string_

---
