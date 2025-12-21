## Problem: Select By ID

### HackerRank Link
https://www.hackerrank.com/challenges/select-by-id/problem

---

### Problem Description
Retrieve all columns (attributes) from the `CITY` table for the row where the city has an `ID` value of **1661**.

---

### Table Description
The `CITY` table contains details of cities, including:
- ID (primary key)
- Name
- Country code
- District
- Population

---

### SQL Query
```sql
SELECT *
FROM CITY
WHERE ID = 1661;
```

---

### Explanation 
- `SELECT *` → fetches **all columns** from the table.
- `FROM CITY` → specifies the table.
- `WHERE ID = 1661` → filters the city with `ID` 1661.

---

### Key Learning
>_Use the `WHERE` clause with a unique identifier (like `ID`) to fetch **exactly one specific row** from a table._

---
