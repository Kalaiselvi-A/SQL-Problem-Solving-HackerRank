## Problem: Revising Aggregations – AVERAGES

### HackerRank Link
https://www.hackerrank.com/challenges/revising-aggregations-the-average-function/problem

---

### Problem Description
Calculate the **average population** of all cities from the `CITY` table where the **District is California**.

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
SELECT AVG(POPULATION)
FROM CITY
WHERE DISTRICT = 'California';
```

---

### Explanation 
- `AVG(POPULATION)` calculates the **average population** of the selected cities.
- `WHERE DISTRICT = 'California'` filters only cities belonging to the California district.
- The query returns a **single aggregated value** representing the average.

---

### Key Learning
> _The `AVG()` aggregate function computes the mean of numeric values, and combining it with `WHERE` allows calculating averages for specific subsets of data._

---
