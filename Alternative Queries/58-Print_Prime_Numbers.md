## Problem: Print Prime Numbers

### HackerRank Link
https://www.hackerrank.com/challenges/print-prime-numbers/problem

---

### Problem Summary

You need to print **all prime numbers less than or equal to 1000**, all on a **single line**, with the **ampersand `&`** character as the separator.

Example for primes ≤ 10: `2&3&5&7`

---

## SQL Query (MySQL)

```sql
SELECT GROUP_CONCAT(n ORDER BY n SEPARATOR '&')
FROM (
    SELECT n
    FROM (
        SELECT @n := @n + 1 AS n
        FROM information_schema.tables t1,
             information_schema.tables t2,
             (SELECT @n := 1) init
        LIMIT 1000
    ) nums
    WHERE n > 1
      AND NOT EXISTS (
          SELECT 1
          FROM (
              SELECT @d := @d + 1 AS d
              FROM information_schema.tables x1,
                   information_schema.tables x2,
                   (SELECT @d := 1) init2
              LIMIT 1000
          ) divs
          WHERE d > 1
            AND d <= SQRT(n)
            AND n % d = 0
      )
) primes;
```

---

### Explanation 
- **Generate numbers from 1 to 1000**
  ```
  SELECT @n := @n + 1 AS n
  FROM information_schema.tables t1,
       information_schema.tables t2,
       (SELECT @n := 1) init
  LIMIT 1000
  ```
  - Uses a **user-defined variable (`@n`)** to create a running sequence
  - Cartesian product of `information_schema.tables` ensures **enough rows**
  - `LIMIT 1000` restricts output to numbers **1 → 1000**
 
- **Exclude non-prime numbers**
  ```
  WHERE n > 1
  AND NOT EXISTS (
      SELECT 1
      FROM (
          SELECT @d := @d + 1 AS d
          FROM information_schema.tables x1,
               information_schema.tables x2,
               (SELECT @d := 1) init2
          LIMIT 1000
      ) divs
      WHERE d > 1
        AND d <= SQRT(n)
        AND n % d = 0
  )
  ```
  - **Logic:**
    - A number is **prime** if:
      - It’s greater than 1
      - It has **no divisors other than 1 and itself**
    - Divisors are checked **only up to √n** (efficient and mathematically correct)
    - `NOT EXISTS` removes any number that has a valid divisor

- **Concatenate the prime numbers**
  ```
  SELECT GROUP_CONCAT(n ORDER BY n SEPARATOR '&')
  ```
  - **Purpose:**
    - Combines all primes into **one line**
    - Ensures ascending order
    - Uses `&` as the separator instead of spaces
  
---

### Key Learning
>- _Use **Cartesian products** to generate sequences in MySQL_
>- _Always check divisors only up to **√n** for prime tests_
>- _Use `GROUP_CONCAT` with `ORDER BY` for deterministic output_
>- _HackerRank requires **one final SELECT result**_

---
