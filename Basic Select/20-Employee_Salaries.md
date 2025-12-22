## Problem: Employee Salaries

### HackerRank Link
https://www.hackerrank.com/challenges/salary-of-employees/problem

---

### Problem Description
Retrieve the **names of employees** from the `Employee` table who:
- Earn **more than 2000** per month, and
- Have worked for the company for **less than 10 months**

The result must be **sorted by ascending `employee_id`**.

---

### Table Description
The `Employee` table contains:
- `employee_id` — Employee ID
- `name` — Employee name
- `months` — Number of months employed
- `salary` — Monthly salary

---

### SQL Query (MySQL)
```sql
SELECT name
FROM Employee
WHERE salary > 2000
  AND months < 10
ORDER BY employee_id;
```

---

### Explanation 
- `WHERE salary > 2000` filters employees with a salary greater than 2000.
- `months < 10` ensures the employee has worked for less than 10 months.
- `AND` combines both conditions.
- `ORDER BY employee_id` sorts the result in **ascending order** of employee ID.

---

### Key Learning
> _Multiple conditions can be combined using `AND` in the `WHERE` clause, and sorting results with `ORDER BY` ensures predictable and readable output._

---
