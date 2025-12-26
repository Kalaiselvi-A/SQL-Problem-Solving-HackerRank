## Problem: New Companies

### HackerRank Link
https://www.hackerrank.com/challenges/the-company/problem

---

### Problem Description
Amber’s corporation has acquired multiple companies, each following a fixed management hierarchy.

For each company, retrieve:
- `company_code`
- `founder`
- Total number of **Lead Managers**
- Total number of **Senior Managers**
- Total number of **Managers**
- Total number of **Employees**

The output must be **sorted by `company_code` in ascending lexicographical order** (string-based sorting).

---

### Table Description

**Company**
- `company_code`
- `founder`

**Lead_Manager**
- `lead_manager_code`
- `company_code`

**Senior_Manager**
- `senior_manager_code`
- `lead_manager_code`
- `company_code`

**Manager**
- `manager_code`
- `senior_manager_code`
- `lead_manager_code`
- `company_code`

**Employee**
- `employee_code`
- `manager_code`
- `senior_manager_code`
- `lead_manager_code`
- `company_code`

> Tables may contain **duplicate records**, so counts must be **distinct**.

---

### SQL Query (MySQL)
```sql
SELECT
    c.company_code,
    c.founder,
    COUNT(DISTINCT lm.lead_manager_code) AS lead_managers,
    COUNT(DISTINCT sm.senior_manager_code) AS senior_managers,
    COUNT(DISTINCT m.manager_code) AS managers,
    COUNT(DISTINCT e.employee_code) AS employees
FROM Company c
LEFT JOIN Lead_Manager lm
    ON c.company_code = lm.company_code
LEFT JOIN Senior_Manager sm
    ON c.company_code = sm.company_code
LEFT JOIN Manager m
    ON c.company_code = m.company_code
LEFT JOIN Employee e
    ON c.company_code = e.company_code
GROUP BY c.company_code, c.founder
ORDER BY c.company_code;
```

---

### Explanation 
- `LEFT JOIN` ensures companies are included even if some hierarchy levels are missing.
- `COUNT(DISTINCT ...)` avoids incorrect counts due to duplicate records.
- `GROUP BY company_code, founder` aggregates all hierarchy levels per company.
- `ORDER BY company_code` sorts results lexicographically (string-based).
  
---

### Key Learning
>- _Using `COUNT(DISTINCT ...)` with multiple `LEFT JOIN`s helps accurately summarize hierarchical data while preventing duplication caused by relational joins._

---
