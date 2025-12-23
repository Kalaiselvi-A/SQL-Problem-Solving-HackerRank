## Problem: Average Population

### HackerRank Link
https://www.hackerrank.com/challenges/average-population/problem

---

### Problem Description
Calculate the **average population** of all cities in the `CITY` table and **round it down to the nearest integer**.

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
SELECT FLOOR(AVG(POPULATION))
FROM CITY;
```

---

### Explanation 
- `AVG(POPULATION)` computes the average population of all cities.
- `FLOOR()` rounds the result **down to the nearest integer**.
- The query returns a **single integer value**.

---

### Key Learning
> _Numeric functions like `FLOOR()` can be combined with aggregate functions to control the format and precision of calculated results._

---
