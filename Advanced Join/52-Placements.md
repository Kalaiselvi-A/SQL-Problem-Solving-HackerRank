## Problem: Placements

### HackerRank Link
https://www.hackerrank.com/challenges/placements/problem

---

### Problem Description
You are given three tables:

- **Students(ID, Name)**
- **Friends(ID, Friend_ID)** → each student has exactly one best friend
- **Packages(ID, Salary)** → salary offered (in $ thousands per month)

---

### Objective
Print the **names of students whose best friends received a higher salary than them**.

### Ordering Rules
- Order names by the **salary offered to their best friends (ascending)**
- Salaries are unique (no ties)

---

### SQL Query

```sql
SELECT s.Name
FROM Students s
JOIN Friends f
    ON s.ID = f.ID
JOIN Packages p_self
    ON s.ID = p_self.ID
JOIN Packages p_friend
    ON f.Friend_ID = p_friend.ID
WHERE p_friend.Salary > p_self.Salary
ORDER BY p_friend.Salary;
```

---

### Explanation 
- **Join Students and Friends**
    ```
      JOIN Friends f ON s.ID = f.ID
    ```
  - Links each student to their **best friend**
- **Get Student’s Salary**
    ```
   JOIN Packages p_self ON s.ID = p_self.ID
    ```
  - Fetches the salary offered to the student
- **Get Friend’s Salary**
    ```
    JOIN Packages p_friend ON f.Friend_ID = p_friend.ID
    ```
  - Fetches the salary offered to the best friend
- **Filter Condition**
    ```
    WHERE p_friend.Salary > p_self.Salary
    ```
  - Select only students whose **friend earns more than them**
- **Ordering**
    ```
    ORDER BY p_friend.Salary
    ```
  - Sorts output based on **best friend’s salary (ascending)**
  
---

### Key Learning
>- _Multiple self-joins help compare related records_
>- _Aliasing (`p_self`, `p_friend`) improves query clarity_
>- _Sorting can be done using columns not present in SELECT_
>- _Understanding relationship tables is crucial in joins_

---
