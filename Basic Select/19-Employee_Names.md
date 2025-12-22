## Problem: Employee Names

### HackerRank Link
https://www.hackerrank.com/challenges/name-of-employees/problem

---

### Problem Description
Retrieve a list of **employee names** from the `Employee` table and display them in **alphabetical order**.

---

### Table Description
The `Employee` table contains:
- `employee_id` — Employee ID
- `name` — Employee name
- `months` — Number of months worked
- `salary` — Monthly salary

---

### SQL Query (MySQL)
```sql
SELECT name
FROM Employee
ORDER BY name;
```

---

### Explanation 
- `SELECT name` retrieves only the employee names.
- `ORDER BY name` sorts the names in **ascending alphabetical order** by default.

---

### Key Learning
> _The `ORDER BY` clause is used to sort query results, and by default, it arranges values in ascending order._

---
