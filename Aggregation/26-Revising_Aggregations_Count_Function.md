## Problem: Revising Aggregations – The COUNT Function

### HackerRank Link
https://www.hackerrank.com/challenges/revising-aggregations-the-count-function/problem

---

### Problem Description
Retrieve the **count of cities** from the `CITY` table whose **population is greater than 100,000**.

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
SELECT COUNT(*)
FROM CITY
WHERE POPULATION > 100000;
```

---

### Explanation 
- `COUNT(*)` returns the **total number of rows** that match the condition.
- `WHERE POPULATION > 100000` filters cities with population greater than 100,000.
- The query returns a **single numeric value** representing the count.

---

### Key Learning
> _Aggregate functions like `COUNT()` are used to summarize data, and combining them with `WHERE` allows counting records that satisfy specific conditions._

---
