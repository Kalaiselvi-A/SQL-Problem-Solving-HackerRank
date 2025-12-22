## Problem: Type of Triangle

### HackerRank Link
https://www.hackerrank.com/challenges/what-type-of-triangle/problem

---

### Problem Description
For each record in the `TRIANGLES` table, identify the **type of triangle** formed using the three side lengths `A`, `B`, and `C`.

The output must be one of the following:
- **Equilateral** — All three sides are equal
- **Isosceles** — Any two sides are equal
- **Scalene** — All three sides are different
- **Not A Triangle** — The given sides cannot form a valid triangle

---

### Table Description
The `TRIANGLES` table contains:
- `A` — Length of side A
- `B` — Length of side B
- `C` — Length of side C

Each row represents one triangle.

---

### SQL Query (MySQL)
```sql
SELECT
CASE
    WHEN A + B <= C OR A + C <= B OR B + C <= A THEN 'Not A Triangle'
    WHEN A = B AND B = C THEN 'Equilateral'
    WHEN A = B OR B = C OR A = C THEN 'Isosceles'
    ELSE 'Scalene'
END
FROM TRIANGLES;
```

---

### Explanation 
- The **triangle inequality rule** is checked first:
  - If the sum of any two sides is less than or equal to the third side, a triangle cannot be formed.
- If all **three** sides are **equal**, the triangle is **Equilateral**.
- If any **two** sides are **equal**, the triangle is **Isosceles**.
- If **all** sides are **different**, the triangle is **Scalene**.
- The `CASE` statement evaluates conditions **top-to-bottom**, so order matters.

---

### Key Learning
> _The `CASE` statement enables conditional logic in SQL, and **ordering** conditions correctly is crucial when multiple rules must be evaluated._

---
