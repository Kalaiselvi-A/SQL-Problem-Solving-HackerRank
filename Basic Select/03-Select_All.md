## Problem: Select All

### HackerRank Link
https://www.hackerrank.com/challenges/select-all-sql/problem

---

### Problem Description
The task is to retrieve **all columns (attributes)** for **every row** present in the `CITY` table without applying any filtering conditions.

---

### Table Description
The `CITY` table contains details of cities, including:
- City name
- Country code
- District
- Population

---

### SQL Query
```sql
SELECT *
FROM CITY;
```

---

### Explanation 
- `SELECT *` → retrieves **all columns** from the CITY table.
- Since no `WHERE` clause is used, the query returns **every row** in the table.
- This query is useful when the complete dataset is required.

---

### Key Learning
>_`SELECT *` is used to retrieve all columns from a table when you need the complete dataset._

---
