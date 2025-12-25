## Problem: Challenges

### HackerRank Link
https://www.hackerrank.com/challenges/challenges/problem

---

### Problem Description
Julia asked students to create coding challenges.  
We need to find **how many challenges each student created** and filter them as follows:

1. Print `hacker_id`, `name`, and `total_challenges`
2. Sort by:
   - Descending `total_challenges`
   - Ascending `hacker_id` if counts are equal
3. Exclude students who **tie below the maximum count** (only include all students if they have the **maximum number of challenges** or their count is unique)

---

### Table Relationships
- `Hackers.hacker_id = Challenges.hacker_id`
- Each hacker may have created **zero or more challenges**

---

### SQL Query (MySQL)

```sql
WITH ChallengeCount AS (
    SELECT 
        H.hacker_id,
        H.name,
        COUNT(C.challenge_id) AS total_challenges
    FROM Hackers H
    LEFT JOIN Challenges C
        ON H.hacker_id = C.hacker_id
    GROUP BY H.hacker_id, H.name
),
MaxCount AS (
    SELECT MAX(total_challenges) AS max_challenges
    FROM ChallengeCount
)
SELECT hacker_id, name, total_challenges
FROM ChallengeCount
WHERE total_challenges = (SELECT max_challenges FROM MaxCount)
   OR total_challenges NOT IN (
       SELECT total_challenges
       FROM ChallengeCount
       GROUP BY total_challenges
       HAVING COUNT(*) > 1
   )
ORDER BY total_challenges DESC, hacker_id ASC;
```

---

### Explanation 
- **CTE** `ChallengeCount`
  - Counts how many challenges each hacker created
  - Uses `LEFT JOIN` to include hackers with 0 challenges
- **CTE** `MaxCount`
  - Finds the **maximum number of challenges created** by any hacker
- **Filtering**
  - Include:
    - Students who created the **maximum number of challenges**
    - Students whose count is **unique** (not tied with others below max)
- **Ordering**
  - `ORDER BY total_challenges DESC, hacker_id ASC`

---

### Key Learning
>- _Using `WITH` (CTEs) helps break complex queries into logical steps._
>- _`HAVING COUNT(*) > 1` identifies duplicate counts._
>- _Combining `MAX()` and exclusion logic helps meet the “tie but exclude below max” requirement._

---
