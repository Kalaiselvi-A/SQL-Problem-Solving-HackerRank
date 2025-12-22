## Problem: Binary Tree Nodes

### HackerRank Link
https://www.hackerrank.com/challenges/binary-search-tree-1/problem

---

### Problem Description
You are given a table `BST` with two columns:
- `N` — Value of the node
- `P` — Parent value of the node

For each node, determine its **type**:
- **Root** → If the node has no parent
- **Leaf** → If the node has no children
- **Inner** → If the node is neither root nor leaf

The output must be **ordered by node value (`N`)**.

---

### Table Description
The `BST` table contains:
- `N` — Node value
- `P` — Parent node value (`NULL` for root)

---

### SQL Query (MySQL)
```sql
SELECT
    N,
    CASE
        WHEN P IS NULL THEN 'Root'
        WHEN N NOT IN (SELECT DISTINCT P FROM BST WHERE P IS NOT NULL) THEN 'Leaf'
        ELSE 'Inner'
    END AS NodeType
FROM BST
ORDER BY N;
```

---

### Explanation 
- `P IS NULL` identifies the **root node**.
- The subquery:
    `SELECT DISTINCT P FROM BST WHERE P IS NOT NULL`
  returns all nodes that act as **parents**.
- If a node `N` does **not appear as a parent**, it has no children → **Leaf**.
- Any node that has both a parent and at least one child is classified as **Inner**.
- `ORDER BY N` ensures nodes are printed in ascending order.

---

### Key Learning
> _Subqueries combined with `CASE` expressions allow classification of hierarchical data such as trees by analyzing parent–child relationships._

---
