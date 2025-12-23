## Problem: The Blunder

### HackerRank Link
https://www.hackerrank.com/challenges/the-blunder/problem

---

### Problem Description
Samantha calculated the **average salary** after accidentally removing all `0`s from employee salaries.  
We need to find the **difference between the actual average salary and the incorrect average salary**, then **round it up to the nearest integer**.

---

### Table Description
The `EMPLOYEES` table contains:
- `ID` — Employee ID  
- `NAME` — Employee name  
- `SALARY` — Monthly salary  

---

### SQL Query (MySQL)
```sql
SELECT CEILING(
    AVG(SALARY) - AVG(REPLACE(SALARY, '0', ''))
)
FROM EMPLOYEES;
```

---

### Explanation 
- `AVG(SALARY)` → Calculates the **actual average salary**
- `REPLACE(SALARY, '0', '')` → Removes all `0`s from the salary (Samantha’s mistake)
- `AVG(REPLACE(...))` → Calculates the **incorrect average salary**
- Subtracting both gives the **error**
- `CEILING()` → Rounds the result **up to the nearest integer**, as required

---

### Key Learning
>- _`REPLACE()` can be used to manipulate numeric data as strings._
>- _`CEILING()` ensures rounding up to the next integer._
>- _Aggregate functions like `AVG()` can be applied to expressions, not just columns._

---
