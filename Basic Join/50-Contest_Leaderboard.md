## Problem: Contest Leaderboard

### HackerRank Link
https://www.hackerrank.com/challenges/contest-leaderboard/problem

---

### Problem Description
Each hacker can submit multiple solutions for the same challenge.  
Only the **maximum score per challenge** should be counted.

The **total score of a hacker** is defined as:
> Sum of the **maximum score** obtained by that hacker for **each challenge**.

---

### Requirements
1. Calculate total score for each hacker.
2. Exclude hackers whose total score is **0**.
3. Sort results by:
   - Descending total score
   - Ascending hacker_id (if scores are equal)

---

### Tables Used
- **Hackers(hacker_id, name)**
- **Submissions(submission_id, hacker_id, challenge_id, score)**

---

### SQL Query (MySQL)

```sql
SELECT
    h.hacker_id,
    h.name,
    SUM(ms.max_score) AS total_score
FROM Hackers h
JOIN (
    SELECT
        hacker_id,
        challenge_id,
        MAX(score) AS max_score
    FROM Submissions
    GROUP BY hacker_id, challenge_id
) ms
ON h.hacker_id = ms.hacker_id
GROUP BY h.hacker_id, h.name
HAVING SUM(ms.max_score) > 0
ORDER BY total_score DESC, h.hacker_id ASC;
```

---

### Explanation 
- **Find best score per challenge**
    ```
      MAX(score)
    ```
  - A hacker may submit many times.
  - Only the **highest score per challenge** is taken.
- **Subquery**
    ```
    FROM Submissions
    GROUP BY hacker_id, challenge_id
    ```
  - Groups submissions by hacker and challenge.
  - Prevents counting multiple submissions for the same challenge.
- **Join with Hackers table**
    ```
    JOIN Hackers h ON h.hacker_id = ms.hacker_id
    ```
  - Fetches the hacker’s name along with scores.
- **Calculate total score**
    ```
    SUM(ms.max_score)
    ```
  - Adds all maximum challenge scores for each hacker.
- **GROUP BY**
    ```
    GROUP BY h.hacker_id, h.name
    ```
  - Ensures one row per hacker.
- **HAVING clause**
    ```
    HAVING SUM(ms.max_score) > 0
    ```
  - Removes hackers with **zero total score.**
  - `HAVING` is used because filtering is done after aggregation.
- **ORDER BY**
    ```
    ORDER BY total_score DESC, h.hacker_id ASC
    ```
  - Highest score first.
  - If scores are equal, smaller `hacker_id` comes first.
  
---

### Key Learning
>- _Use `MAX()` to select the best attempt when multiple submissions exist._
>- _Apply **proper** `GROUP BY` to avoid double counting._
>- _Prefer **subqueries over CTEs** in HackerRank MySQL._
>- _Use `HAVING` for filtering aggregated results._
>- _**Join tables** to enrich results with descriptive data._
>- _Apply **correct ordering** to handle ties accurately._

---
