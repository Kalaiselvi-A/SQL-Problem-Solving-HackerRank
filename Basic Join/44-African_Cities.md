## Problem: African Cities

### HackerRank Link
https://www.hackerrank.com/challenges/african-cities/problem

---

### Problem Description
You are given two tables: `CITY` and `COUNTRY`.

Your task is to:
- Retrieve the **names of all cities**
- Consider **only cities that belong to countries in the continent 'Africa'**

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
SELECT CITY.Name
FROM CITY
JOIN COUNTRY
ON CITY.CountryCode = COUNTRY.Code
WHERE COUNTRY.Continent = 'Africa';
```

---

### Explanation 
- `JOIN` combines `CITY` and `COUNTRY` tables using matching country codes.
- `WHERE COUNTRY.Continent = 'Africa'` filters only African countries.
- `SELECT CITY.Name` outputs the names of cities located in Africa.
- The result may contain **multiple rows**, each representing one city.

---

### Key Learning
>- _Using JOINs enables filtering data based on attributes stored in another table._
>- _This approach is essential when working with relational databases._

---
