## Problem: Population Density Difference

### HackerRank Link
https://www.hackerrank.com/challenges/population-density-difference/problem

---

### Problem Description
Query the **difference between the maximum and minimum populations** in the `CITY` table.

---

### Table Description
The `CITY` table contains:
- `ID` — City ID  
- `NAME` — City name  
- `COUNTRYCODE` — Country code  
- `DISTRICT` — District  
- `POPULATION` — Population of the city  

---

### SQL Query (MySQL)
```sql
SELECT MAX(POPULATION) - MIN(POPULATION)
FROM CITY;
```

---

### Explanation 
- `MAX(POPULATION)` retrieves the **highest population** value.
- `MIN(POPULATION)` retrieves the **lowest population** value.
- Subtracting them gives the **population density difference**.

---

### Key Learning
> _Aggregate functions like `MAX()` and `MIN()` can be combined in a single query to compute differences across an entire dataset._

---
