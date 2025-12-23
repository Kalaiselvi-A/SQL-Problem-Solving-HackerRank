## Problem: Revising Aggregations – The SUM Function

### HackerRank Link
https://www.hackerrank.com/challenges/revising-aggregations-sum/problem

---

### Problem Description
Calculate the **total population** of all cities from the `CITY` table where the **District is California**.

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
WHERE DISTRICT = 'California';
```

---

### Explanation 
- `SUM(POPULATION)` calculates the **total population** of selected cities.
- `WHERE DISTRICT = 'California'` filters only cities belonging to the California district.
- The query returns a **single aggregated value**.

---

### Key Learning
> _The `SUM()` aggregate function is used to compute totals across numeric columns, and `WHERE` helps limit aggregation to specific conditions._

---
