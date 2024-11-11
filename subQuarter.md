### **Subqueries in SQL:**

A **subquery** is a query within another query. It can return a single value or multiple rows, and is often used in `WHERE`, `HAVING`, or `FROM` clauses to filter data or derive new columns based on the results of another query. Subqueries are typically used when you need to fetch data that will be used as part of the main query.

There are two main types of subqueries in SQL:

1. **Single-Row Subquery**
2. **Multi-Row Subquery**

Additionally, subqueries can be classified based on their placement:

- **Correlated Subquery**
- **Non-Correlated Subquery**

### **1. Single-Row Subquery:**

A **single-row subquery** returns only one row and one column. It's typically used in the `WHERE` clause to compare the result of the subquery with a single value in the main query.

#### Syntax for Single-Row Subquery:

```sql
SELECT column1, column2
FROM table_name
WHERE column1 = (SELECT column3 FROM table_name WHERE condition);
```

#### Example 1: Single-Row Subquery (using `=`)

```sql
SELECT Name, Salary
FROM Employees
WHERE DepartmentID = (SELECT DepartmentID FROM Departments WHERE DepartmentName = 'Sales');
```

- **Explanation**: This query retrieves the `Name` and `Salary` of employees who work in the 'Sales' department. The subquery `(SELECT DepartmentID FROM Departments WHERE DepartmentName = 'Sales')` returns the `DepartmentID` for the 'Sales' department, which is then used in the outer query to filter employees.

#### Example 2: Single-Row Subquery (using `BETWEEN`)

```sql
SELECT Name, Salary
FROM Employees
WHERE Salary BETWEEN (SELECT MIN(Salary) FROM Employees WHERE DepartmentID = 1) AND (SELECT MAX(Salary) FROM Employees WHERE DepartmentID = 1);
```

- **Explanation**: This query retrieves the `Name` and `Salary` of employees whose salaries are between the minimum and maximum salary within department 1. The subqueries calculate the `MIN` and `MAX` salaries for department 1.

---

### **2. Multi-Row Subquery:**

A **multi-row subquery** returns more than one row. It's often used with operators such as `IN`, `ANY`, or `ALL` in the `WHERE` clause.

#### Syntax for Multi-Row Subquery:

```sql
SELECT column1, column2
FROM table_name
WHERE column1 IN (SELECT column3 FROM table_name WHERE condition);
```

#### Example 1: Multi-Row Subquery (using `IN`)

```sql
SELECT Name, DepartmentID
FROM Employees
WHERE DepartmentID IN (SELECT DepartmentID FROM Departments WHERE DepartmentName IN ('Sales', 'Marketing'));
```

- **Explanation**: This query retrieves the `Name` and `DepartmentID` of employees who work in either the 'Sales' or 'Marketing' department. The subquery returns the `DepartmentID`s of these two departments, and the outer query selects employees who belong to those departments.

#### Example 2: Multi-Row Subquery (using `ANY`)

```sql
SELECT Name, Salary
FROM Employees
WHERE Salary > ANY (SELECT Salary FROM Employees WHERE DepartmentID = 2);
```

- **Explanation**: This query retrieves the `Name` and `Salary` of employees whose salary is greater than any salary within department 2. The subquery returns the list of salaries for employees in department 2, and the outer query selects employees whose salary exceeds at least one of those.

---

### **3. Correlated Subquery:**

A **correlated subquery** references columns from the outer query. It is executed once for each row processed by the outer query. The subquery depends on the outer query for its values.

#### Syntax for Correlated Subquery:

```sql
SELECT column1, column2
FROM table_name1 outer
WHERE column1 = (SELECT column3 FROM table_name2 inner WHERE inner.column = outer.column);
```

#### Example 1: Correlated Subquery

```sql
SELECT e.Name, e.Salary
FROM Employees e
WHERE e.Salary > (SELECT AVG(Salary) FROM Employees WHERE DepartmentID = e.DepartmentID);
```

- **Explanation**: This query retrieves the `Name` and `Salary` of employees whose salary is higher than the average salary within their own department. The subquery calculates the average salary for each department, and for each employee, the outer query checks if their salary is greater than that average.

#### Example 2: Correlated Subquery

```sql
SELECT e.Name, e.Salary
FROM Employees e
WHERE e.Salary > (SELECT MAX(Salary) FROM Employees WHERE DepartmentID = e.DepartmentID AND e.Salary < 10000);
```

- **Explanation**: This query retrieves the `Name` and `Salary` of employees whose salary is higher than the maximum salary within their department, considering only those employees whose salary is less than 10,000.

---

### **4. Non-Correlated Subquery:**

A **non-correlated subquery** is a subquery that does not reference any columns from the outer query. It is executed once and the result is passed to the outer query.

#### Syntax for Non-Correlated Subquery:

```sql
SELECT column1, column2
FROM table_name
WHERE column1 = (SELECT column3 FROM table_name WHERE condition);
```

#### Example 1: Non-Correlated Subquery

```sql
SELECT Name, Salary
FROM Employees
WHERE DepartmentID = (SELECT DepartmentID FROM Departments WHERE DepartmentName = 'HR');
```

- **Explanation**: This query retrieves the `Name` and `Salary` of employees who work in the 'HR' department. The subquery returns the `DepartmentID` for the 'HR' department, and the outer query filters employees based on that `DepartmentID`.

#### Example 2: Non-Correlated Subquery

```sql
SELECT Name, DepartmentID
FROM Employees
WHERE Salary > (SELECT AVG(Salary) FROM Employees);
```

- **Explanation**: This query retrieves the `Name` and `DepartmentID` of employees whose salary is greater than the average salary of all employees. The subquery calculates the overall average salary, and the outer query compares each employee's salary to this average.

---

### **Key Points to Remember:**

- **Single-Row Subquery**: Returns only one value (a single row and column).
- **Multi-Row Subquery**: Returns multiple rows and is used with `IN`, `ANY`, or `ALL`.
- **Correlated Subquery**: Depends on the outer query for values and is executed for each row.
- **Non-Correlated Subquery**: Does not depend on the outer query and is executed only once.
  
Subqueries allow you to write more complex SQL queries and often provide a more readable and maintainable way to structure queries.
