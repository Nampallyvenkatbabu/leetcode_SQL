# 176. Second Highest Salary

![Difficulty](https://img.shields.io/badge/Difficulty-Medium-orange)
![Language](https://img.shields.io/badge/Language-SQL-blue)

## 🔗 Problem

**LeetCode:** https://leetcode.com/problems/second-highest-salary/

### Problem Statement

Given the `Employee` table, find the **second highest distinct salary**.

If there is no second highest salary, return **NULL**.

---

## 💡 Intuition

To find the second highest distinct salary:

- Find the highest salary.
- Ignore all rows having that highest salary.
- Among the remaining salaries, find the maximum salary.
- If no salary remains, `MAX()` returns `NULL`.

---

## 🚀 Approach

1. Use a subquery to find the highest salary.
2. Filter salaries that are less than the highest salary.
3. Apply `MAX()` on the remaining salaries.
4. Rename the output column as `SecondHighestSalary`.

---

## ✅ SQL Solution

```sql
SELECT MAX(salary) AS SecondHighestSalary
FROM Employee
WHERE salary < (
    SELECT MAX(salary)
    FROM Employee
);
```

---

## 🧪 Example

### Input

| id | salary |
|----|--------|
|1|100|
|2|200|
|3|300|

### Step 1: Highest Salary

```text
300
```

### Step 2: Salaries Less Than Highest

```text
100
200
```

### Step 3: Maximum of Remaining Salaries

```text
200
```

### Output

| SecondHighestSalary |
|---------------------|
| 200 |

---

## 🧪 Example 2

### Input

| id | salary |
|----|--------|
|1|100|

### Step 1: Highest Salary

```text
100
```

### Step 2: Salaries Less Than Highest

```text
No rows
```

### Output

| SecondHighestSalary |
|---------------------|
| NULL |

---

## 🔑 Key Takeaways

- `MAX()` returns the highest value.
- The subquery finds the highest salary.
- `WHERE salary < (highest salary)` removes the maximum salary.
- Applying `MAX()` again returns the second highest **distinct** salary.
- If no second highest salary exists, `MAX()` on an empty set returns `NULL`.

---

## 🏷 Tags

`SQL` `Subquery` `Aggregate Functions` `MAX()` `LeetCode`
