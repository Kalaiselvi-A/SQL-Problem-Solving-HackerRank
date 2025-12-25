## Problem: The Report

### HackerRank Link
https://www.hackerrank.com/challenges/the-report/problem

---

### Problem Description
You are given two tables: `Students` and `Grades`.

Your task is to generate a report with the following columns:
- `Name`
- `Grade`
- `Marks`

#### Rules:
1. Students with **Grade ≥ 8**:
   - Display their **actual names**
   - Sort by **Grade (descending)**
   - If grades are the same, sort by **Name (alphabetically)**

2. Students with **Grade < 8**:
   - Display `"NULL"` as the name
   - Sort by **Grade (descending)**
   - If grades are the same, sort by **Marks (ascending)**

---

### Table Description

#### Students
- `ID` — Student ID
- `Name` — Student name
- `Marks` — Marks obtained

#### Grades
- `Grade` — Grade value
- `Min_Mark` — Minimum mark for the grade
- `Max_Mark` — Maximum mark for the grade

---

### SQL Query (MySQL)

```sql
SELECT 
    CASE 
        WHEN G.Grade < 8 THEN 'NULL'
        ELSE S.Name
    END AS Name,
    G.Grade,
    S.Marks
FROM Students S
JOIN Grades G
ON S.Marks BETWEEN G.Min_Mark AND G.Max_Mark
ORDER BY 
    G.Grade DESC,
    CASE 
        WHEN G.Grade >= 8 THEN S.Name
        ELSE S.Marks
    END ASC;
```

---

### Explanation 
- `JOIN` matches students to grades using the marks range.
- `CASE`:
  - Replaces student names with `"NULL"` when grade is below 8.
- `ORDER BY` logic:
  - Sorts by **Grade descending**
  - For grades ≥ 8 → sorts by **Name**
  - For grades < 8 → sorts by **Marks**
- This satisfies all formatting and ordering conditions.

---

### Key Learning
>- _Conditional logic using `CASE` allows dynamic column values and sorting behavior._
>- _Combining `CASE` with `ORDER BY` enables complex reporting requirements in SQL._

---
