## Problem: Interviews

### HackerRank Link
https://www.hackerrank.com/challenges/interviews/problem

---

### Problem Description
Samantha runs contests for candidates at multiple colleges. You are given the following tables:

- **Contests(contest_id, hacker_id, name)**
- **Colleges(college_id, contest_id)**
- **Challenges(challenge_id, college_id)**
- **View_Stats(challenge_id, total_views, total_unique_views)**
- **Submission_Stats(challenge_id, total_submissions, total_accepted_submission)**

**Task:**  
For each contest, output:

- `contest_id`, `hacker_id`, `name`  
- Sum of `total_submissions`, `total_accepted_submissions`, `total_views`, `total_unique_views`  

**Exclude contests** where all four sums are 0.  
Sort results by `contest_id`.

---

### SQL Query

```sql
SELECT
    c.contest_id,
    c.hacker_id,
    c.name,
    SUM(ss.total_submissions) AS total_submissions,
    SUM(ss.total_accepted_submissions) AS total_accepted_submissions,
    SUM(vs.total_views) AS total_views,
    SUM(vs.total_unique_views) AS total_unique_views
FROM Contests c
JOIN Colleges co
    ON c.contest_id = co.contest_id
JOIN Challenges ch
    ON co.college_id = ch.college_id
LEFT JOIN (
    SELECT
        challenge_id,
        SUM(total_submissions) AS total_submissions,
        SUM(total_accepted_submissions) AS total_accepted_submissions
    FROM Submission_Stats
    GROUP BY challenge_id
) ss
    ON ch.challenge_id = ss.challenge_id
LEFT JOIN (
    SELECT
        challenge_id,
        SUM(total_views) AS total_views,
        SUM(total_unique_views) AS total_unique_views
    FROM View_Stats
    GROUP BY challenge_id
) vs
    ON ch.challenge_id = vs.challenge_id
GROUP BY
    c.contest_id, c.hacker_id, c.name
HAVING
    SUM(
        COALESCE(ss.total_submissions, 0) +
        COALESCE(ss.total_accepted_submissions, 0) +
        COALESCE(vs.total_views, 0) +
        COALESCE(vs.total_unique_views, 0)
    ) > 0
ORDER BY c.contest_id;
```

---

### Explanation 
- **Start from Contest → College → Challenge**
    ```
    FROM Contests c
    JOIN Colleges co ON c.contest_id = co.contest_id
    JOIN Challenges ch ON co.college_id = ch.college_id
    ```
  - A contest has **many colleges**
  - Each college has **many challenges**
  - This chain gives **all challenges belonging to a contest**
- **Aggregate Submission stats before joining**
    ```
    LEFT JOIN (
      SELECT challenge_id,
             SUM(total_submissions) AS total_submissions,
             SUM(total_accepted_submissions) AS total_accepted_submissions
      FROM Submission_Stats
      GROUP BY challenge_id
    ) ss ON ch.challenge_id = ss.challenge_id
    ```
  - `Submission_Stats` can have **multiple rows per challenge**
  - Direct join causes **duplicate counting**
  - Pre-aggregation ensures **1 row per challenge**
- **Aggregate View stats before joining**
    ```
    LEFT JOIN (
      SELECT challenge_id,
             SUM(total_views) AS total_views,
             SUM(total_unique_views) AS total_unique_views
      FROM View_Stats
      GROUP BY challenge_id
    ) vs ON ch.challenge_id = vs.challenge_id
    ```
  - Same reason as submissions — avoids **row multiplication**.
- **Sum values per contest**
    ```
    GROUP BY c.contest_id, c.hacker_id, c.name
    ```
  - Combines all challenges under one contest
  - Produces **one row per contest**
- **Remove contests with zero activity**
    ```
    HAVING SUM(
      COALESCE(ss.total_submissions,0) +
      COALESCE(ss.total_accepted_submissions,0) +
      COALESCE(vs.total_views,0) +
      COALESCE(vs.total_unique_views,0)
    ) > 0
    ```
  - `COALESCE` converts NULL → 0
  - `HAVING` filters after aggregation
  - Removes contests with **no submissions & no views**
- **Final Output Order**
    ```
    ORDER BY c.contest_id;
    ```
  
---

### Key Learning
>- _Pre-aggregate data **before joining** to prevent row duplication and inflated results._
>- _Understand and follow the **data hierarchy** (Contest → College → Challenge → Stats)._
>- _Use `LEFT JOIN` to retain parent records even when child data is missing._
>- _Apply `HAVING`, not `WHERE`, to filter on aggregated values._
>- _Handle missing data safely using `COALESCE` to avoid NULL impact on calculations._
>- _Group only at the **required business level** (contest level in this case)._
>- _Avoid **reserved keywords** when naming aliases or subqueries._
>- _Advanced SQL problems test **logical correctness**, not just syntax._

---
