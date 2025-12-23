## Problem: Top Earners

### HackerRank Link
https://www.hackerrank.com/challenges/earnings-of-employees/problem

---

### Problem Description
Each employee's **total earnings** is calculated as:
      `total_earnings = salary × months`

You need to:
1. Find the **maximum total earnings** among all employees.
2. Find the **number of employees** who have earned this maximum amount.
3. Print both values as **two space-separated integers**.

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
SELECT 
    months * salary AS earnings,
    COUNT(*) 
FROM Employee
GROUP BY earnings
ORDER BY earnings DESC
LIMIT 1;
```

---

### Explanation 
- `months * salary` → Calculates **total earnings** per employee
- `GROUP BY earnings` → Groups employees having the same earnings
- `COUNT(*)` → Counts how many employees share that earnings value
- `ORDER BY earnings DESC` → Sorts earnings from highest to lowest
- `LIMIT 1` → Returns only the **maximum earnings row**

---

### Key Learning
>- _Arithmetic expressions can be directly used in `SELECT`._
>- _`GROUP BY` works with calculated columns._
>- _`ORDER BY ... DESC LIMIT 1` is a common pattern to find maximum values._
>- _**Aggregation + grouping** helps answer ranking-based questions efficiently._

---
