## Problem: 15 Days of Learning SQL

### HackerRank Link
https://www.hackerrank.com/challenges/15-days-of-learning-sql/problem

---

### Problem Summary

You are given:

- **Hackers(hacker_id, name)**
- **Submissions(submission_id, hacker_id, submission_date, score)**

**Task:** For each day of the contest (March 01–15, 2016):

1. Count **unique hackers who made at least one submission each day so far** (starting from the first day).  
2. Identify the hacker who made the **maximum submissions** that day (lowest hacker_id in case of tie).  
3. Output columns: `submission_date`, `unique_hackers`, `hacker_id`, `name`  
4. Order by `submission_date`.

---

### SQL Query

```sql
SELECT
    S1.submission_date,
    (
        SELECT COUNT(DISTINCT S2.hacker_id)
        FROM Submissions S2
        WHERE S2.submission_date = S1.submission_date
          AND (
                SELECT COUNT(DISTINCT S3.submission_date)
                FROM Submissions S3
                WHERE S3.hacker_id = S2.hacker_id
                  AND S3.submission_date < S1.submission_date
              ) = DATEDIFF(S1.submission_date, '2016-03-01')
    ),
    (
        SELECT S2.hacker_id
        FROM Submissions S2
        WHERE S2.submission_date = S1.submission_date
        GROUP BY S2.hacker_id
        ORDER BY COUNT(*) DESC, S2.hacker_id
        LIMIT 1
    ),
    (
        SELECT H.name
        FROM Hackers H
        WHERE H.hacker_id = (
            SELECT S2.hacker_id
            FROM Submissions S2
            WHERE S2.submission_date = S1.submission_date
            GROUP BY S2.hacker_id
            ORDER BY COUNT(*) DESC, S2.hacker_id
            LIMIT 1
        )
    )
FROM
    (SELECT DISTINCT submission_date FROM Submissions) S1
ORDER BY
    S1.submission_date;
```

---

### Explanation 
- **Get all contest days**
    ```
    SELECT DISTINCT submission_date FROM Submissions
    ```
  - Creates a list of all unique submission dates.
  - The outer query will process each date individually.
- **Count consistent hackers**
    ```
    SELECT COUNT(DISTINCT S2.hacker_id)
    FROM Submissions S2
    WHERE S2.submission_date = S1.submission_date
      AND (
            SELECT COUNT(DISTINCT S3.submission_date)
            FROM Submissions S3
            WHERE S3.hacker_id = S2.hacker_id
              AND S3.submission_date < S1.submission_date
          ) = DATEDIFF(S1.submission_date, '2016-03-01')
    ```
  - For each date:
    1. Look at all hackers who submitted on that day (`S2`).
    2. For each hacker, count how many **previous days they submitted** (`S3`).
    3. Compare it to the **number of days since the contest start** using `DATEDIFF`.
       - This ensures the hacker has submitted **every day without missing**.
  - `COUNT(DISTINCT S2.hacker_id)` gives the number of consistent hackers.
- **Find the top hacker of the day**
    ```
    SELECT S2.hacker_id
    FROM Submissions S2
    WHERE S2.submission_date = S1.submission_date
    GROUP BY S2.hacker_id
    ORDER BY COUNT(*) DESC, S2.hacker_id
    LIMIT 1
    ```
  - Groups submissions by hacker for that day.
  - Orders by **number of submissions** in descending order.
  - If there’s a tie, the hacker with the **lowest ID** is chosen.
  - Returns the `hacker_id` of the top contributor.
- **Get the hacker’s name**
    ```
    SELECT H.name
    FROM Hackers H
    WHERE H.hacker_id = (top_hacker_id)
    ```
  - Uses the `hacker_id` from Step 3 to fetch the **hacker’s name** from the `Hackers` table.
  
---

### Key Learning
>- _Uses **correlated subqueries** for:_
>  - _Counting consistent hackers._
>  - _Finding the top hacker per day._
>- _Uses `DATEDIFF` to track consecutive days._
>- _Orders final output by `submission_date`._

---
