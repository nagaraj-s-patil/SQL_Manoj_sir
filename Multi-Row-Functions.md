# **Multi-Row Functions:-**
Here's an explanation with syntax examples for some **Miscellaneous Functions** in SQL:

### 1. **`NVL()`**
   - **Purpose:** Replaces `NULL` values with a specified replacement value.
   - **Syntax:** 
     ```sql
     NVL(expression, replacement_value)
     ```
   - **Example:**
     ```sql
     SELECT NVL(salary, 0) AS salary FROM employees;
     ```
     In this example, if the `salary` column contains `NULL`, it will be replaced by `0`.

### 2. **`NULLIF()`**
   - **Purpose:** Compares two expressions and returns `NULL` if they are equal; otherwise, it returns the first expression.
   - **Syntax:** 
     ```sql
     NULLIF(expression1, expression2)
     ```
   - **Example:**
     ```sql
     SELECT NULLIF(salary, 0) AS salary FROM employees;
     ```
     If the `salary` is `0`, `NULL` will be returned, otherwise, the actual `salary` value is returned.

### 3. **`COALESCE()`**
   - **Purpose:** Returns the first non-null value in a list of expressions.
   - **Syntax:**
     ```sql
     COALESCE(expression1, expression2, ..., expressionN)
     ```
   - **Example:**
     ```sql
     SELECT COALESCE(phone_number, 'No Phone') AS phone FROM customers;
     ```
     If `phone_number` is `NULL`, it returns `'No Phone'` as the default value.

### 4. **`DECODE()`**
   - **Purpose:** Performs conditional logic, similar to a `CASE` statement, but in a more concise manner.
   - **Syntax:**
     ```sql
     DECODE(expression, search1, result1, search2, result2, ..., default_result)
     ```
   - **Example:**
     ```sql
     SELECT DECODE(department_id, 10, 'Accounting', 20, 'Sales', 'Other') AS department_name
     FROM employees;
     ```
     If the `department_id` is `10`, it returns `'Accounting'`; if `20`, it returns `'Sales'`; otherwise, it returns `'Other'`.

### 5. **`CASE`**
   - **Purpose:** Evaluates conditions and returns specific values based on those conditions (more flexible than `DECODE`).
   - **Syntax:**
     ```sql
     CASE 
        WHEN condition1 THEN result1
        WHEN condition2 THEN result2
        ELSE default_result
     END
     ```
   - **Example:**
     ```sql
     SELECT CASE 
               WHEN salary > 5000 THEN 'High'
               WHEN salary BETWEEN 3000 AND 5000 THEN 'Medium'
               ELSE 'Low'
             END AS salary_range
     FROM employees;
     ```
     This checks the `salary` and categorizes it into `'High'`, `'Medium'`, or `'Low'`.

---
