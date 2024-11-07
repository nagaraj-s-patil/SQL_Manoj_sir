In SQL, **joins** are used to combine rows from two or more tables based on a related column. There are different types of joins: **INNER JOIN**, **LEFT JOIN**, **RIGHT JOIN**, and **FULL JOIN**.

### 1. **INNER JOIN**
This returns rows that have matching values in both tables. If there is no match, the row is not included in the result.

**Syntax:**
```sql
SELECT column1, column2, ...
FROM table1
INNER JOIN table2
ON table1.common_column = table2.common_column;
```

**Example:**
```sql
SELECT employees.name, departments.department_name
FROM employees
INNER JOIN departments
ON employees.department_id = departments.department_id;
```
This query will return the names of employees and their respective department names, only if the employee has a matching department.

---

### 2. **LEFT JOIN (or LEFT OUTER JOIN)**
This returns all rows from the left table and the matching rows from the right table. If there is no match, NULL values are returned for columns of the right table.

**Syntax:**
```sql
SELECT column1, column2, ...
FROM table1
LEFT JOIN table2
ON table1.common_column = table2.common_column;
```

**Example:**
```sql
SELECT employees.name, departments.department_name
FROM employees
LEFT JOIN departments
ON employees.department_id = departments.department_id;
```
This query will return all employees and their department names. If an employee does not belong to any department, `NULL` will be shown for the department name.

---

### 3. **RIGHT JOIN (or RIGHT OUTER JOIN)**
This returns all rows from the right table and the matching rows from the left table. If there is no match, NULL values are returned for columns of the left table.

**Syntax:**
```sql
SELECT column1, column2, ...
FROM table1
RIGHT JOIN table2
ON table1.common_column = table2.common_column;
```

**Example:**
```sql
SELECT employees.name, departments.department_name
FROM employees
RIGHT JOIN departments
ON employees.department_id = departments.department_id;
```
This query will return all departments and their employees. If a department has no employees, `NULL` will be shown for the employee's name.

---

### 4. **FULL JOIN (or FULL OUTER JOIN)**
This returns all rows when there is a match in either left (table1) or right (table2). It returns NULL on the side where there is no match.

**Syntax:**
```sql
SELECT column1, column2, ...
FROM table1
FULL JOIN table2
ON table1.common_column = table2.common_column;
```

**Example:**
```sql
SELECT employees.name, departments.department_name
FROM employees
FULL JOIN departments
ON employees.department_id = departments.department_id;
```
This query will return all employees and all departments. If an employee does not belong to a department or if a department has no employees, `NULL` will be shown in the respective column.

---

These are the basic types of joins used in SQL, each serving different purposes depending on whether you want to include unmatched rows from one or both tables.
