## Problem: Ollivander's Inventory

### HackerRank Link
https://www.hackerrank.com/challenges/harry-potter-and-wands/problem

---

### Problem Description
Ron wants to buy **non-evil wands** that require the **minimum number of gold galleons** for each combination of **power and age**.

You must print:
- `id`
- `age`
- `coins_needed`
- `power`

---

### Conditions
1. Consider **only non-evil wands** → `is_evil = 0`
2. For each `(power, age)` combination:
   - Select the wand with **minimum coins_needed**
3. Sorting rules:
   - Descending order of **power**
   - If power is same, descending order of **age**

---

### Table Relationships
- `Wands.code = Wands_Property.code`
- Each `code` maps to **exactly one age**

---

### SQL Query (MySQL)

```sql
SELECT 
    W.id,
    P.age,
    W.coins_needed,
    W.power
FROM Wands W
JOIN Wands_Property P
    ON W.code = P.code
WHERE P.is_evil = 0
AND W.coins_needed = (
    SELECT MIN(W2.coins_needed)
    FROM Wands W2
    JOIN Wands_Property P2
        ON W2.code = P2.code
    WHERE 
        W2.power = W.power
        AND P2.age = P.age
        AND P2.is_evil = 0
)
ORDER BY 
    W.power DESC,
    P.age DESC;
```

---

### Explanation 
1. **Join Tables**
    - `WHERE COUNTRY.Continent = 'Asia'` filters only Asian countries.
2. **Filter Non-Evil Wands**
    - `WHERE P.is_evil = 0`
3. **Subquery for Minimum Cost**
    - For `each (power, age)` pair:
      - Find the minimum `coins_needed`
          ```
          SELECT MIN(W2.coins_needed)
          ```
4. **Match Only Cheapest Wand**
    - Ensures only the cheapest wand per `(power, age)` is selected
5. **Sorting**
    - `ORDER BY power DESC, age DESC`

---

### Key Learning
>- _Correlated subqueries are powerful when you need the minimum or maximum value per group without using GROUP BY._
>- _This problem demonstrates how to filter grouped results while still returning complete row data._

---
