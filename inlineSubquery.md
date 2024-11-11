An **inline subquery** (also known as a **correlated subquery** or **scalar subquery**) is a subquery that is written directly within a **SELECT**, **INSERT**, **UPDATE**, or **DELETE** statement, often used for filtering or deriving a value to be used by the outer query.

### **Definition:**
An inline subquery is a subquery that is placed within the `SELECT`, `FROM`, or `WHERE` clause of a query. It returns a single value or a set of values that the outer query can use.

- **Inline Subquery in `SELECT` Clause**: It is used to calculate or derive values for each row in the result set.
- **Inline Subquery in `WHERE` Clause**: It is used for filtering rows based on the result of a subquery.
- **Inline Subquery in `FROM` Clause**: It is used as a virtual table or derived table for the outer query.

### **Types of Inline Subqueries:**

1. **Scalar Subquery (Single Value)**: 
   A scalar subquery returns a single value (single row, single column) and can be used wherever a single value is expected (like in the `SELECT` or `WHERE` clause).

2. **Multiple-Row Subquery**:
   This subquery returns multiple rows and can be used with operators like `IN`, `ANY`, or `ALL`.

---

### **Syntax of Inline Subqueries:**

#### **1. Inline Subquery in `SELECT` Clause:**

```sql
SELECT column1, 
       (SELECT MAX(salary) FROM employees WHERE department_id = d.department_id) AS max_salary
FROM departments d;
```

- In this example, the subquery inside the `SELECT` clause calculates the maximum salary for each department.

#### **2. Inline Subquery in `WHERE` Clause:**

```sql
SELECT employee_id, first_name, last_name, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

- Here, the subquery returns the average salary from the `employees` table, and the outer query filters for employees with a salary greater than the average.

#### **3. Inline Subquery in `FROM` Clause (Derived Table)**:

```sql
SELECT department_id, AVG(salary)
FROM (SELECT department_id, salary FROM employees WHERE salary > 50000) AS high_salary_employees
GROUP BY department_id;
```

- This example uses an inline subquery in the `FROM` clause to create a temporary table (`high_salary_employees`) and then performs an aggregation on it in the outer query.

---

### **Examples of Inline Subqueries:**

#### **1. Inline Subquery in `SELECT` Clause (Scalar Subquery):**

```sql
SELECT first_name, 
       (SELECT MAX(salary) FROM employees WHERE department_id = 10) AS max_salary
FROM employees
WHERE department_id = 10;
```

- The subquery `(SELECT MAX(salary) FROM employees WHERE department_id = 10)` returns the highest salary for department 10, and it will be displayed next to each employee in that department.

#### **2. Inline Subquery in `WHERE` Clause (Multiple-Row Subquery):**

```sql
SELECT first_name, last_name, salary
FROM employees
WHERE department_id IN (SELECT department_id FROM departments WHERE location_id = 1400);
```

- The inner subquery returns a list of `department_id` values for departments located in location 1400, and the outer query retrieves employees who work in those departments.

#### **3. Inline Subquery in `FROM` Clause (Derived Table):**

```sql
SELECT department_id, COUNT(*) AS num_employees
FROM (SELECT department_id FROM employees WHERE hire_date > '2023-01-01') AS new_employees
GROUP BY department_id;
```

- The inline subquery in the `FROM` clause selects employees hired after January 1, 2023, and the outer query counts how many new employees exist in each department.

---

### **Key Points About Inline Subqueries:**

- **Scalar Subqueries**: These are subqueries that return a single value. They are often used in the `SELECT` or `WHERE` clauses.
- **Multiple-Row Subqueries**: These subqueries can return multiple rows, and they are typically used with operators such as `IN`, `ANY`, `ALL`, etc.
- **Performance Considerations**: Inline subqueries can sometimes lead to performance issues if the subquery is executed for each row of the outer query. It's essential to consider performance optimization strategies such as indexing and query restructuring.
- **Correlated Subqueries**: An inline subquery can be correlated, meaning it refers to a column from the outer query. In this case, the subquery is executed for each row of the outer query.

---

### **Conclusion:**
Inline subqueries are powerful tools for writing more complex SQL queries. They allow you to:
- Perform calculations within the `SELECT` clause.
- Filter rows in the `WHERE` clause based on dynamic conditions.
- Use derived tables within the `FROM` clause.

By embedding subqueries directly into your query structure, you can achieve more flexibility in your SQL operations.
