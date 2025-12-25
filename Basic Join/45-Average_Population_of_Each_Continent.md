## Problem: Average Population of Each Continent

### HackerRank Link
https://www.hackerrank.com/challenges/average-population-of-each-continent/problem

---

### Problem Description
You are given two tables: `CITY` and `COUNTRY`.

Your task is to:
- Retrieve the **name of each continent**
- Calculate the **average population of cities** in each continent
- **Round down** the average population to the **nearest integer**

**Note:**  
`CITY.CountryCode` and `COUNTRY.Code` are matching key columns.

---

### Table Description

#### CITY
- `ID` — City ID
- `Name` — City name
- `CountryCode` — Country code
- `Population` — City population

#### COUNTRY
- `Code` — Country code
- `Name` — Country name
- `Continent` — Continent name

---

### SQL Query (MySQL)

```sql
SELECT COUNTRY.Continent,
       FLOOR(AVG(CITY.Population))
FROM CITY
JOIN COUNTRY
ON CITY.CountryCode = COUNTRY.Code
GROUP BY COUNTRY.Continent;
```

---

### Explanation 
- `JOIN` links `CITY` and `COUNTRY` tables using matching country codes.
- `AVG(CITY.Population)` computes the average city population per continent.
- `FLOOR()` rounds the average **down to the nearest integer**.
- `GROUP BY COUNTRY.Continent` ensures one result per continent.
- The query outputs **continent name and its average city population**.

---

### Key Learning
>- _Combining `JOIN`, `GROUP BY`, and aggregate functions like `AVG()` enables continent-wise analysis._
>- _`FLOOR()` is useful when rounding down numerical results as required by problem constraints._

---
