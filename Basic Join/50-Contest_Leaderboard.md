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
WITH MaxScores AS (
    SELECT
        hacker_id,
        challenge_id,
        MAX(score) AS max_score
    FROM Submissions
    GROUP BY hacker_id, challenge_id
)
SELECT
    H.hacker_id,
    H.name,
    SUM(M.max_score) AS total_score
FROM Hackers H
JOIN MaxScores M
    ON H.hacker_id = M.hacker_id
GROUP BY H.hacker_id, H.name
HAVING SUM(M.max_score) > 0
ORDER BY total_score DESC, H.hacker_id ASC;
```

---

### Explanation 
- **CTE** `MaxScores`
    ```
    SELECT hacker_id, challenge_id, MAX(score)
    FROM Submissions
    GROUP BY hacker_id, challenge_id
    ```
  - Ensures **only the highest score per challenge** is considered for each hacker.
- **Join with Hackers**
    ```
    JOIN Hackers H
      ON H.hacker_id = M.hacker_id
    ```
  - Retrieves the hacker’s name for final output.
- **Calculate Total Score** `SUM(M.max_score)`
  - Adds maximum scores across all challenges attempted by the hacker.
- **Exclude Zero Scores** `HAVING SUM(M.max_score) > 0`
  - Removes hackers who never earned any points.
- **Sorting** `ORDER BY total_score DESC, hacker_id ASC`
  - Matches HackerRank’s required ordering.

---

### Key Learning
>- _Use `MAX(score)` to avoid counting multiple submissions for the same challenge._
>- _CTEs make complex leaderboard logic easier to read and debug._
>- _`HAVING` filters aggregated results after `GROUP BY`._
>- _Always re-check sorting conditions in HackerRank problems._

---
