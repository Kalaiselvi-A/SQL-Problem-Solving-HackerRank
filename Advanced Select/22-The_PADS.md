## Problem: The PADS

### HackerRank Link
https://www.hackerrank.com/challenges/the-pads/problem

---

### Problem Description
Generate **two result sets** from the `OCCUPATIONS` table:

1. Display an **alphabetically ordered list of names**, each followed by the **first letter of their occupation** enclosed in parentheses.
2. Display the **count of each occupation**, sorted by:
   - Ascending number of occurrences
   - Alphabetical order of occupation (if counts are equal)

Each count should be displayed in the following format:
  ```
  There are a total of [occupation_count] [occupation]s.
  ```

---

### Table Description
The `OCCUPATIONS` table contains:
- `Name` — Person's name
- `Occupation` — One of the following:
  - Doctor
  - Professor
  - Singer
  - Actor

---

## SQL Query 1: Names with Occupation Initial

```sql
SELECT CONCAT(Name, '(', LEFT(Occupation, 1), ')')
FROM OCCUPATIONS
ORDER BY Name;
```
### Explanation 
- `LEFT(Occupation, 1)` extracts the **first character** of the occupation.
- `CONCAT()` combines the **name and occupation initial** in the required format `Name(O)`.
- `ORDER BY Name` ensures **alphabetical ordering** of names.

## SQL Query 2: Occupation Count Summary

```sql
SELECT CONCAT(
    'There are a total of ',
    COUNT(*),
    ' ',
    LOWER(Occupation),
    's.'
)
FROM OCCUPATIONS
GROUP BY Occupation
ORDER BY COUNT(*), Occupation;
```
### Explanation 
- `COUNT(*)` calculates the number of people per occupation.
- `LOWER(Occupation)` converts the occupation name to lowercase.
- `GROUP BY` Occupation groups records by occupation.
- `ORDER BY COUNT(*), Occupation` sorts first by count (ascending), then alphabetically.

---

### Key Learning
> _Use **`CONCAT`, `GROUP BY`, and `ORDER BY` together** to format text output and perform **custom sorting** directly in SQL without extra processing._

---
