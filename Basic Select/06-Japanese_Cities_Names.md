## Problem: Japanese Cities Names

### HackerRank Link
https://www.hackerrank.com/challenges/japanese-cities-name/problem

---

### Problem Description
Retrieve the **names of all cities** from the `CITY` table that are located in **Japan**.  
The `COUNTRYCODE` for Japan is `JPN`.

---

### Table Description
The `CITY` table contains city information, including:
- ID
- Name
- Country code
- District
- Population

---

### SQL Query
```sql
SELECT NAME
FROM CITY
WHERE COUNTRYCODE = 'JPN';
```

---

### Explanation 
- `SELECT NAME` → Retrieves only the city names
- `FROM CITY` → Specifies the table
- `WHERE COUNTRYCODE = 'JPN'` → Filters cities that belong to Japan

---

### Key Learning
>_Understanding how to filter and fetch required columns from a database table using SQL._

---
