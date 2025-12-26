## Problem: SQL Project Planning

### HackerRank Link
https://www.hackerrank.com/challenges/sql-projects/problem

---

### Problem Description
You are given a table **Projects** with:
- `Task_ID`
- `Start_Date`
- `End_Date`

Each task lasts exactly **1 day**.

If tasks have **consecutive End_Date values**, they belong to the **same project**.

---

### Objective
1. Identify all distinct projects.
2. For each project, determine:
   - Project start date
   - Project end date
3. Sort the result by:
   - Number of days taken (ascending)
   - Project start date (ascending, if days are equal)

---

### SQL Query (MySQL)

```sql
WITH ProjectGroups AS (
    SELECT
        Start_Date,
        End_Date,
        DATE_SUB(Start_Date, INTERVAL 
            ROW_NUMBER() OVER (ORDER BY Start_Date) DAY
        ) AS grp
    FROM Projects
)
SELECT
    MIN(Start_Date) AS project_start,
    MAX(End_Date) AS project_end
FROM ProjectGroups
GROUP BY grp
ORDER BY
    DATEDIFF(MAX(End_Date), MIN(Start_Date)) ASC,
    project_start ASC;
```

---

### Explanation 
- **Assign Project Groups**
    ```
      ROW_NUMBER() OVER (ORDER BY Start_Date)
    ```
  - Assigns a sequential number to each task.
    ```
      DATE_SUB(Start_Date, INTERVAL ROW_NUMBER() DAY)
    ```
  - Creates a **constant value (`grp`)** for consecutive dates.
  - Tasks with consecutive dates get grouped into the **same project**.
- **Group Tasks into Projects**
    ```
    GROUP BY grp
    ```
  - Combines consecutive tasks into a single project.
- **Get Project Start and End Dates**
    ```
    MIN(Start_Date) → project_start
    MAX(End_Date)   → project_end
    ```
- **Sort Output**
    ```
    ORDER BY
      DATEDIFF(project_end, project_start),
      project_start;
    ```
  - First by project duration (ascending)
  - Then by start date (ascending)
  
---

### Key Learning
>- _Window functions help detect consecutive records_
>- _`ROW_NUMBER()` is useful for sequence-based grouping_
>- _Date arithmetic simplifies project duration calculations_
>- _Always re-check ordering conditions in HackerRank problems_

---
