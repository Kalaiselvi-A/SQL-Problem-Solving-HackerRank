## Problem: Higher Than 75 Marks

### HackerRank Link
https://www.hackerrank.com/challenges/more-than-75-marks/problem

---

### Problem Description
Retrieve the **names of students** from the `STUDENTS` table who have scored **more than 75 marks**.

The output should be:
1. **Ordered by the last three characters** of each student's name.
2. If multiple students share the same last three characters, sort them by **ascending ID**.

---

### Table Description
The `STUDENTS` table contains:
- `ID` — Student ID
- `NAME` — Student name (only alphabetic characters)
- `MARKS` — Student marks

---

### SQL Query (MySQL)
```sql
SELECT NAME
FROM STUDENTS
WHERE MARKS > 75
ORDER BY RIGHT(NAME, 3), ID;
```

---

### Explanation 
- `Marks > 75` → filters eligible students
- `RIGHT(Name, 3)` → sorts by the **last three characters** of the name
- `ID` → secondary sorting when last three characters are the same
- Output shows only the **Name** column as required

---

### Key Learning
> _Use `RIGHT(column, n)` **in** `ORDER BY` to sort results based on the **last characters of a string**, with a secondary sort to handle ties cleanly._

---
