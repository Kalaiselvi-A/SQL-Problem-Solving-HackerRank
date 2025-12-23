## Problem: Japan Population

### HackerRank Link
https://www.hackerrank.com/challenges/japan-population/problem

---

### Problem Description
Calculate the **total population** of all cities in the `CITY` table where the **country code is Japan (JPN)**.

---

### Table Description
The `CITY` table contains:
- `ID` — City ID
- `NAME` — City name
- `COUNTRYCODE` — Country code
- `DISTRICT` — District name
- `POPULATION` — Population of the city

---

### SQL Query (MySQL)
```sql
SELECT SUM(POPULATION)
FROM CITY
WHERE COUNTRYCODE = 'JPN';
```

---

### Explanation 
- `SUM(POPULATION)` calculates the **total population**.
- `WHERE COUNTRYCODE = 'JPN'` filters only Japanese cities.
- The query returns a single aggregated value.

---

### Key Learning
> _The `SUM()` aggregate function is used to calculate totals, and filtering with `WHERE` allows aggregation on specific subsets of data._

---
