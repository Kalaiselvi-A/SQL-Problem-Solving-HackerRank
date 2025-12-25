## Problem: Top Competitors

### HackerRank Link
https://www.hackerrank.com/challenges/full-score/problem

---

### Problem Description
You are given contest-related tables:
- `Hackers`
- `Difficulty`
- `Challenges`
- `Submissions`

Your task is to print the **hacker_id** and **name** of hackers who achieved **full scores in more than one challenge**.

---

### Conditions
1. A **full score** means:
   - `Submissions.score = Difficulty.score`
2. A hacker must achieve full score in **more than one distinct challenge**
3. Output order:
   - Descending order of **number of full-score challenges**
   - If tied, sort by **ascending hacker_id**

---

### Table Relationships
- `Challenges.difficulty_level = Difficulty.difficulty_level`
- `Submissions.challenge_id = Challenges.challenge_id`
- `Submissions.hacker_id = Hackers.hacker_id`

---

### SQL Query (MySQL)

```sql
SELECT 
    H.hacker_id,
    H.name
FROM Hackers H
JOIN Submissions S 
    ON H.hacker_id = S.hacker_id
JOIN Challenges C 
    ON S.challenge_id = C.challenge_id
JOIN Difficulty D 
    ON C.difficulty_level = D.difficulty_level
WHERE S.score = D.score
GROUP BY H.hacker_id, H.name
HAVING COUNT(DISTINCT S.challenge_id) > 1
ORDER BY 
    COUNT(DISTINCT S.challenge_id) DESC,
    H.hacker_id ASC;
```

---

### Explanation 
- `Joins` connect `hackers` → `submissions` → `challenges` → `difficulty`.
- `WHERE S.score = D.score` filters **only full-score submissions**.
- `COUNT(DISTINCT S.challenge_id)` ensures:
  - Multiple submissions for the same challenge are counted once.
- `HAVING` filters hackers with **more than one full-score challenge**.
- `ORDER BY` applies the required sorting logic.

---

### Key Learning
>- _Using `HAVING` with `COUNT(DISTINCT ...)` is essential when filtering grouped results._
>- _This problem demonstrates how multi-table joins and aggregate functions work together to identify qualifying records accurately._

---
