In SQL, `ROWNUM` and `ROWID` are two pseudo-columns used in certain databases like Oracle. These are not regular columns that you explicitly define in a `CREATE TABLE` statement but are automatically created by the database system for each row in a table. Let's explore both `ROWNUM` and `ROWID` in detail:

### **1. `ROWNUM` in SQL (Oracle)**

- **Definition**: `ROWNUM` is a pseudo-column in Oracle that assigns a unique number to each row returned by a query, starting from 1 for the first row and incrementing by 1 for each subsequent row. It is useful for limiting the number of rows returned or for creating a row count in a query result.
- **Usage**: `ROWNUM` is usually used in conjunction with a `SELECT` statement to limit the number of rows in a query result.

#### **Syntax:**

```sql
SELECT ROWNUM, column1, column2
FROM table_name;
```

- **`ROWNUM`** will be returned alongside the actual data (columns) in the table.

#### **Examples:**

1. **Basic Example of `ROWNUM`:**

```sql
SELECT ROWNUM, first_name, last_name 
FROM employees;
```

This query will display the row number (`ROWNUM`) along with the `first_name` and `last_name` for each employee.

2. **Limiting Results Using `ROWNUM`:**

```sql
SELECT * 
FROM employees
WHERE ROWNUM <= 5;
```

This query retrieves only the first 5 rows from the `employees` table. It uses `ROWNUM` to limit the output.

#### **Important Points about `ROWNUM`:**
- **Order of rows**: `ROWNUM` does not guarantee any specific order of rows unless explicitly ordered by using `ORDER BY`. It is assigned before any `ORDER BY` clause is applied.
- **Usage with `ORDER BY`**: To get specific rows in a certain order, you need to use a subquery:

```sql
SELECT * 
FROM (SELECT * FROM employees ORDER BY salary DESC) 
WHERE ROWNUM <= 5;
```

This query retrieves the top 5 highest-paid employees by first sorting the employees by salary in descending order and then applying `ROWNUM`.

---

### **2. `ROWID` in SQL (Oracle)**

- **Definition**: `ROWID` is a unique identifier for every row in a database table. It represents the physical address of the row in the database storage. `ROWID` is unique to each row and is assigned automatically by the Oracle database.
- **Usage**: `ROWID` is often used for quickly identifying and accessing rows. It can also be used for performance optimization in some cases.

#### **Syntax:**

```sql
SELECT ROWID, column1, column2 
FROM table_name;
```

#### **Examples:**

1. **Basic Example of `ROWID`:**

```sql
SELECT ROWID, first_name, last_name
FROM employees;
```

This query will return the unique `ROWID` for each row in the `employees` table along with the `first_name` and `last_name`.

2. **Using `ROWID` to Delete Duplicate Rows:**

```sql
DELETE FROM employees 
WHERE ROWID NOT IN (SELECT MIN(ROWID) FROM employees GROUP BY first_name, last_name);
```

This query deletes duplicate records from the `employees` table. It keeps the first instance of each duplicate (based on `first_name` and `last_name`) and removes the others. `ROWID` is used to uniquely identify and delete the duplicates.

3. **Using `ROWID` to Update Rows Efficiently:**

```sql
UPDATE employees
SET salary = salary * 1.1
WHERE ROWID = 'AAAO7TAAEAAAAFlAAD';
```

In this case, `ROWID` is used to update a specific row with a known `ROWID`.

#### **Important Points about `ROWID`:**
- **Uniqueness**: Each row in a table has a unique `ROWID` within the table.
- **Physical Location**: `ROWID` represents the physical storage location of the row in the database (data block address), and it is often used for performance optimization.
- **No Changes to `ROWID`**: `ROWID` values cannot be altered as they are automatically assigned by the database and are based on the physical storage of data.

---

### **Key Differences Between `ROWNUM` and `ROWID`:**

| **Feature**     | **ROWNUM**                             | **ROWID**                                    |
|-----------------|----------------------------------------|----------------------------------------------|
| **Definition**  | A sequential number assigned to each row in the result set. | A unique identifier for each row in the database table. |
| **Usage**       | Used for limiting results and generating row numbers. | Used for quickly identifying a row and accessing it. |
| **Uniqueness**  | Not unique across queries. The same row in different queries can have different `ROWNUM` values. | Unique to every row in the database. |
| **Modification**| Cannot be modified. | Cannot be modified. |
| **Order**       | `ROWNUM` is assigned before `ORDER BY`. | `ROWID` is always unique, regardless of the order. |

---

### **Conclusion:**

- **`ROWNUM`**: Useful for numbering rows in a result set and limiting the number of rows returned. It is assigned before any sorting is applied.
- **`ROWID`**: A unique identifier for each row in a table, pointing to the physical location of the row in storage. It is typically used for fast access to rows.

These pseudo-columns are specific to Oracle databases, and their usage can significantly improve performance and flexibility in SQL queries.
