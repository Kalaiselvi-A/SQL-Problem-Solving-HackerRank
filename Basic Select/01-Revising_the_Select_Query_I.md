## Problem: Revising the Select Query

### HackerRank Link
https://www.hackerrank.com/challenges/revising-the-select-query/problem

---

### Problem Description
The task is to retrieve **all columns** from the `CITY` table for cities that meet the following conditions:
- The city is located in **America**
- The population of the city is **greater than 100,000**

The `CountryCode` for America is represented as `USA`.

---

### Table Description
The `CITY` table contains information about cities, including:
- City name
- Country code
- District
- Population

---

### SQL Query
```sql
SELECT *
FROM CITY
WHERE COUNTRYCODE = 'USA'
  AND POPULATION > 100000;
```

---

### Explanation 
- `SELECT *` → fetches **all columns** from the CITY table.
- `COUNTRYCODE = 'USA'` → filters only **American cities**.
- `POPULATION > 100000` → selects cities with population **greater than 100,000**.
- `AND` → ensures **both conditions** are satisfied.

---

### Key Learning
>Combining multiple conditions using the `WHERE` clause improves data filtering accuracy.

---
