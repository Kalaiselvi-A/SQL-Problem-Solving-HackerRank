## Problem: Japanese Cities Attributes

### HackerRank Link
https://www.hackerrank.com/challenges/japanese-cities-attributes/problem

---

### Problem Description
Retrieve all attributes (columns) from the `CITY` table for cities located in **Japan**.  
The `COUNTRYCODE` for Japan is `JPN`.

---

### Table Description
The `CITY` table includes information about cities, such as:
- ID
- Name
- Country code
- District
- Population

---

### SQL Query
```sql
SELECT *
FROM CITY
WHERE COUNTRYCODE = 'JPN';
```

---

### Explanation 
- `SELECT *` → Selects all columns from the table.
- `FROM CITY` → Specifies the table to query.
- `WHERE COUNTRYCODE = 'JPN'` → Filters rows to include only those cities in Japan.

---

### Key Learning
>_Use `SELECT *` with a `WHERE` clause to filter rows based on a condition, retrieving all attributes of only the relevant records._

---
