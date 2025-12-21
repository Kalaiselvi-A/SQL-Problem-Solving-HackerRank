## Problem: Revising the Select Query II

### HackerRank Link
https://www.hackerrank.com/challenges/revising-the-select-query-2/problem

---

### Problem Description
The task is to retrieve the **names of cities** from the `CITY` table that satisfy the following conditions:
- The city is located in **America**
- The population of the city is **greater than 120,000**

The country code for America is represented as `USA`.

---

### Table Description
The `CITY` table stores city-related information such as:
- Name of the city
- Country code
- District
- Population

---

### SQL Query
```sql
SELECT NAME
FROM CITY
WHERE COUNTRYCODE = 'USA'
  AND POPULATION > 120000;
```

---

### Explanation 
- `SELECT NAME` → fetches only the city names
- `FROM CITY` → data source table
- `COUNTRYCODE = 'USA'` → filters American cities
- `POPULATION > 120000` → selects cities with population greater than 120,000

---

### Key Learning
>_Filtering data effectively using the `WHERE` clause with multiple conditions (`AND`) helps retrieve precise and meaningful results from a database._

---
