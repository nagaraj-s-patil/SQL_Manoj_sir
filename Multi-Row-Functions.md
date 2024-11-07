![Uploading image.png…]()

# **Multi-Row Functions:-**
Here’s an explanation and examples of various **Miscellaneous Functions** in SQL, focusing on commonly used ones:

### 1. **`NVL()`**
   - **Purpose:** Replaces `NULL` with a specified value.
   - **Syntax:**
     ```sql
     NVL(expression, replacement_value)
     ```
   - **Example:**
     ```sql
     SELECT NVL(salary, 0) FROM employees;
     ```
     - **Explanation:** If the `salary` is `NULL`, it will return `0` instead.

### 2. **`NULLIF()`**
   - **Purpose:** Returns `NULL` if two expressions are equal, otherwise returns the first expression.
   - **Syntax:**
     ```sql
     NULLIF(expression1, expression2)
     ```
   - **Example:**
     ```sql
     SELECT NULLIF(salary, 0) FROM employees;
     ```
     - **Explanation:** If the `salary` is `0`, it will return `NULL`. Otherwise, it will return the `salary`.

### 3. **`COALESCE()`**
   - **Purpose:** Returns the first non-`NULL` value in the list of expressions.
   - **Syntax:**
     ```sql
     COALESCE(expression1, expression2, ..., expressionN)
     ```
   - **Example:**
     ```sql
     SELECT COALESCE(commission, salary, 0) FROM employees;
     ```
     - **Explanation:** This will return the `commission` if it is not `NULL`, otherwise, it checks `salary`. If both are `NULL`, it returns `0`.

### 4. **`DECODE()`**
   - **Purpose:** Performs conditional logic similar to `CASE` but in a simpler form.
   - **Syntax:**
     ```sql
     DECODE(expression, search_value, result1, result2, ..., default_value)
     ```
   - **Example:**
     ```sql
     SELECT DECODE(department_id, 10, 'HR', 20, 'Finance', 'Other') FROM employees;
     ```
     - **Explanation:** If `department_id` is `10`, it returns `'HR'`; if `20`, it returns `'Finance'`; otherwise, it returns `'Other'`.

### 5. **`CASE`**
   - **Purpose:** Evaluates conditions and returns a value based on the first condition that is true. Can be used in SQL statements to create conditional logic.
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
            END AS salary_category
     FROM employees;
     ```
     - **Explanation:** This checks the `salary` and categorizes it as `'High'`, `'Medium'`, or `'Low'` based on the given conditions.

### 6. **`GREATEST()`**
   - **Purpose:** Returns the greatest value from a list of expressions.
   - **Syntax:**
     ```sql
     GREATEST(expression1, expression2, ..., expressionN)
     ```
   - **Example:**
     ```sql
     SELECT GREATEST(salary, bonus) FROM employees;
     ```
     - **Explanation:** This returns the larger value between `salary` and `bonus`.

### 7. **`LEAST()`**
   - **Purpose:** Returns the smallest value from a list of expressions.
   - **Syntax:**
     ```sql
     LEAST(expression1, expression2, ..., expressionN)
     ```
   - **Example:**
     ```sql
     SELECT LEAST(salary, bonus) FROM employees;
     ```
     - **Explanation:** This returns the smaller value between `salary` and `bonus`.

### 8. **`IN`**
   - **Purpose:** Checks if a value is within a list of values.
   - **Syntax:**
     ```sql
     expression IN (value1, value2, ..., valueN)
     ```
   - **Example:**
     ```sql
     SELECT * FROM employees WHERE department_id IN (10, 20, 30);
     ```
     - **Explanation:** This returns all employees whose `department_id` is either `10`, `20`, or `30`.

### 9. **`BETWEEN`**
   - **Purpose:** Checks if a value is within a range (inclusive).
   - **Syntax:**
     ```sql
     expression BETWEEN value1 AND value2
     ```
   - **Example:**
     ```sql
     SELECT * FROM employees WHERE salary BETWEEN 3000 AND 5000;
     ```
     - **Explanation:** This returns employees with a `salary` between `3000` and `5000` (inclusive).

### 10. **`ISNULL()`**
   - **Purpose:** Checks if an expression is `NULL`. (Note: This is more common in some SQL implementations like MySQL or SQL Server.)
   - **Syntax:**
     ```sql
     ISNULL(expression)
     ```
   - **Example:**
     ```sql
     SELECT ISNULL(salary, 0) FROM employees;
     ```
     - **Explanation:** If the `salary` is `NULL`, it will return `0`.

### 11. **`CAST()`**
   - **Purpose:** Converts one data type to another.
   - **Syntax:**
     ```sql
     CAST(expression AS data_type)
     ```
   - **Example:**
     ```sql
     SELECT CAST(salary AS VARCHAR(50)) FROM employees;
     ```
     - **Explanation:** This converts `salary` to a string (VARCHAR) of length 50.
