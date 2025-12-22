## Problem: Occupations

### HackerRank Link
https://www.hackerrank.com/challenges/occupations/problem

---

### Problem Description
Pivot the `Occupation` column in the `OCCUPATIONS` table so that:

- Each **Name** is listed under its corresponding **Occupation**
- Names under each occupation are **sorted alphabetically**
- The output contains **four columns** in this exact order:
  1. Doctor
  2. Professor
  3. Singer
  4. Actor
- If an occupation has fewer names than others, display **NULL** for missing values

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

### Core Concept: Pivoting in SQL
Pivoting means **transforming rows into columns**.

MySQL does **not** provide a built-in `PIVOT` operator, so we simulate pivot behavior using:

- **Window Functions** → `ROW_NUMBER()`
- **Conditional Logic** → `CASE WHEN`
- **Aggregation Functions** → `MAX()`

This combination helps convert **row-based data** into **column-based output**.

---

### SQL Query (MySQL - Pivot using ROW_NUMBER)
```sql
SELECT
    MAX(CASE WHEN Occupation = 'Doctor' THEN Name END)     AS Doctor,
    MAX(CASE WHEN Occupation = 'Professor' THEN Name END)  AS Professor,
    MAX(CASE WHEN Occupation = 'Singer' THEN Name END)     AS Singer,
    MAX(CASE WHEN Occupation = 'Actor' THEN Name END)      AS Actor
FROM (
    SELECT Name, Occupation,
           ROW_NUMBER() OVER (PARTITION BY Occupation ORDER BY Name) AS rn
    FROM OCCUPATIONS
) t
GROUP BY rn
ORDER BY rn;
```

---

### Concept Explanation 
- **Pivoting** means converting **rows into columns**
- Each **Occupation** becomes a **separate column**
- Names under each occupation must be **sorted alphabetically**
- `ROW_NUMBER()` assigns a sequence number to each name **within the same occupation**
- This sequence (`rn`) aligns names **row-by-row across columns**
- `CASE WHEN` places each name under its correct occupation column
- `NULL` appears automatically when an occupation has fewer names

**Core Idea:** _Use **row numbers + conditional aggregation** to transform row data into a structured column format._

---

### Query Explanation 
#### INNER QUERY — DATA PREPARATION
```sql
SELECT 
    Name,
    Occupation,
    ROW_NUMBER() OVER (PARTITION BY Occupation ORDER BY Name) AS rn
FROM OCCUPATIONS
```
- `SELECT` → Tells MySQL which columns we want in the result.
- `Name` → Fetches the **Name column** from the table.
- `Occupation` → Fetches the **Occupation column** (Doctor, Professor, Singer, Actor).
- `ROW_NUMBER() OVER (...) AS rn` → Generates a **sequential number** for each row.
  - `OVER (...)` → Defines **how row numbers are calculated**.
  - `PARTITION BY Occupation` → Divides the table into **separate groups** by occupation.
    - Row numbering **restarts from 1** for each occupation.
    - **Example:**
       ```nginx 
      Doctor → 1,2,3
      Singer → 1,2
      Actor → 1,2,3,4
      ```
  - `ORDER BY Name` → Sorts names **alphabetically** inside each occupation **before numbering**.
      (This guarantees: Alphabetical order under each column)
  - `AS rn` → Renames the generated row number column to **rn**. Used later for **grouping**
 
  - **Result of Inner Query (Sample)**
      | Name  | Occupation | rn |
      | ----- | ---------- | -- |
      | Alex  | Doctor     | 1  |
      | Sam   | Doctor     | 2  |
      | Maria | Professor  | 1  |
      | Peter | Professor  | 2  |
      | Meera | Singer     | 1  |
      | Julia | Actor      | 1  |
      | Tom   | Actor      | 2  |

#### OUTER QUERY — PIVOTING DATA
- `SELECT` → Starts the final output selection.
- `MAX(CASE WHEN Occupation = 'Doctor' THEN Name END) AS Doctor`
  - `CASE WHEN Occupation = 'Doctor'` → Checks if the row belongs to **Doctor**
  - `THEN Name` → Returns the name if condition is true
  - `END` → Otherwise returns `NULL`
  - `MAX(...)` → Picks the non-NULL value (only one exists per row number)
  - `AS Doctor` → Column heading is **Doctor**
- **Same Logic Applies To:**
    ```
    MAX(CASE WHEN Occupation = 'Professor' THEN Name END) AS Professor
    MAX(CASE WHEN Occupation = 'Singer' THEN Name END) AS Singer
    MAX(CASE WHEN Occupation = 'Actor' THEN Name END) AS Actor
    ```
    Each creates **one column per occupation.**
  - **Why MAX?**
    - SQL requires an **aggregate function** when using `GROUP BY`
    - Only one name exists per occupation per row number
    - `MAX()` safely returns that name
- FROM Clause
  `FROM (
   ...
) t`
  - Uses the **inner query result**
  - `t` is a **temporary alias**
- GROUP BY `GROUP BY rn`
  - Groups rows by **row number**
  - Aligns:
    - 1st Doctor
    - 1st Professor
    - 1st Singer
    - 1st Actor
  - Forms **one row per rn**
- ORDER BY `ORDER BY rn;`
  - First row → first alphabetic names
  - Second row → second alphabetic names

---

### FINAL OUTPUT STRUCTURE
    | Doctor | Professor | Singer | Actor |
    | ------ | --------- | ------ | ----- |
    | Alex   | Maria     | Meera  | Julia |
    | Sam    | Peter     | NULL   | Tom   |

  Automatically prints **NULL** where data is missing

---

### INTERVIEW SUMMARY 
> _First, I used `ROW_NUMBER()` partitioned by occupation to assign positions to names in alphabetical order. Then I pivoted rows into columns using `CASE WHEN` with aggregation and grouped by the row number._

---

### Key Learning
> _Window functions like `ROW_NUMBER()` combined with conditional aggregation allow pivoting rows into columns even when SQL does not provide a native PIVOT operator._

---




















