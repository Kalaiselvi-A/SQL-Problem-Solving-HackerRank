## Problem: Population Census

### HackerRank Link
https://www.hackerrank.com/challenges/asian-population/problem

---

### Problem Description
You are given two tables: `CITY` and `COUNTRY`.

Your task is to:
- Calculate the **total population of all cities**
- Consider **only cities that belong to countries in the continent 'Asia'**

**Note:**  
`CITY.CountryCode` and `COUNTRY.Code` are matching key columns.

---

### Table Description

#### CITY
- `ID` — City ID
- `Name` — City name
- `CountryCode` — Country code
- `Population` — City population

#### COUNTRY
- `Code` — Country code
- `Name` — Country name
- `Continent` — Continent name

---

### SQL Query (MySQL)

```sql
SELECT SUM(CITY.POPULATION)
FROM CITY
JOIN COUNTRY
ON CITY.CountryCode = COUNTRY.Code
WHERE COUNTRY.Continent = 'Asia';
```

---

### Explanation 
- `JOIN` connects the `CITY` and `COUNTRY` tables using matching country codes.
- `WHERE COUNTRY.Continent = 'Asia'` filters only Asian countries.
- `SUM(CITY.POPULATION)` calculates the total population of all qualifying cities.
- The query returns **a single numeric value**.

---

### Key Learning
>- _INNER JOINs allow combining related data across tables._
>- _Aggregation functions like `SUM()` can then be applied after filtering to compute meaningful totals._

---
