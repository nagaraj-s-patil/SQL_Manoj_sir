# **Single-Row-Functions:-**
Here are some commonly used SQL string functions along with syntax examples:

### 1. **UPPER()**
   - Converts all characters in a string to uppercase.
   - **Syntax:** `UPPER(column_name)`
   - **Example:**
     ```sql
     SELECT UPPER(first_name) AS uppercase_name FROM employees;
     ```
   - **Result:** Converts `first_name` values like `"john"` to `"JOHN"`.

### 2. **LOWER()**
   - Converts all characters in a string to lowercase.
   - **Syntax:** `LOWER(column_name)`
   - **Example:**
     ```sql
     SELECT LOWER(first_name) AS lowercase_name FROM employees;
     ```
   - **Result:** Converts `first_name` values like `"JOHN"` to `"john"`.

### 3. **CONCAT()**
   - Combines two strings into one.
   - **Syntax:** `CONCAT(string1, string2)`
   - **Example:**
     ```sql
     SELECT CONCAT(first_name, ' ', last_name) AS full_name FROM employees;
     ```
   - **Result:** Joins `first_name` and `last_name` with a space in between, like `"John Doe"`.

### 4. **SUBSTR() or SUBSTRING()**
   - Extracts a substring from a string.
   - **Syntax:** `SUBSTR(column_name, start_position, length)`
   - **Example:**
     ```sql
     SELECT SUBSTR(first_name, 1, 3) AS short_name FROM employees;
     ```
   - **Result:** Returns the first 3 characters of `first_name`, so `"John"` becomes `"Joh"`.

### 5. **LENGTH()**
   - Returns the number of characters in a string.
   - **Syntax:** `LENGTH(column_name)`
   - **Example:**
     ```sql
     SELECT LENGTH(first_name) AS name_length FROM employees;
     ```
   - **Result:** Counts the characters in `first_name`, so `"John"` would return `4`.

### 6. **TRIM()**
   - Removes leading and trailing spaces from a string.
   - **Syntax:** `TRIM(column_name)`
   - **Example:**
     ```sql
     SELECT TRIM(first_name) AS trimmed_name FROM employees;
     ```
   - **Result:** If `first_name` is `" John "`, this will return `"John"`.

### 7. **LPAD() and RPAD()**
   - Pads a string on the left (LPAD) or right (RPAD) with specified characters up to a certain length.
   - **Syntax:** 
     - `LPAD(column_name, length, pad_string)`
     - `RPAD(column_name, length, pad_string)`
   - **Example:**
     ```sql
     SELECT LPAD(first_name, 10, '*') AS padded_name FROM employees;
     ```
   - **Result:** Pads `first_name` on the left with `*` up to a length of 10 characters, so `"John"` becomes `"******John"`.

### 8. **INSTR()**
   - Finds the position of a substring within a string.
   - **Syntax:** `INSTR(column_name, substring)`
   - **Example:**
     ```sql
     SELECT INSTR(first_name, 'o') AS position FROM employees;
     ```
   - **Result:** Finds the position of `'o'` in `first_name`, so if `first_name` is `"John"`, it returns `2`.

### 9. **REPLACE()**
   - Replaces occurrences of a substring within a string with another substring.
   - **Syntax:** `REPLACE(column_name, old_string, new_string)`
   - **Example:**
     ```sql
     SELECT REPLACE(first_name, 'o', 'a') AS modified_name FROM employees;
     ```
   - **Result:** Replaces `o` with `a` in `first_name`, so `"John"` becomes `"Jahn"`.
## **Numeric Functions:-**
   Here's a breakdown of common SQL **Numeric Functions** with syntax and examples to illustrate how each one works:

### 1. **`ROUND()`**
   - **Purpose**: Rounds a number to a specified number of decimal places.
   - **Syntax**: `ROUND(number, decimal_places)`
   - **Example**:
     ```sql
     SELECT ROUND(123.4567, 2) AS RoundedNumber;
     ```
     **Result**: `123.46`

### 2. **`TRUNC()`**
   - **Purpose**: Truncates (cuts off) a number to a specified number of decimal places without rounding.
   - **Syntax**: `TRUNC(number, decimal_places)`
   - **Example**:
     ```sql
     SELECT TRUNC(123.4567, 2) AS TruncatedNumber;
     ```
     **Result**: `123.45`

### 3. **`MOD()`**
   - **Purpose**: Returns the remainder of a division between two numbers.
   - **Syntax**: `MOD(number, divisor)`
   - **Example**:
     ```sql
     SELECT MOD(10, 3) AS Modulus;
     ```
     **Result**: `1` (because 10 divided by 3 leaves a remainder of 1)

### 4. **`ABS()`**
   - **Purpose**: Returns the absolute (non-negative) value of a number.
   - **Syntax**: `ABS(number)`
   - **Example**:
     ```sql
     SELECT ABS(-25.5) AS AbsoluteValue;
     ```
     **Result**: `25.5`

### 5. **`CEIL()`**
   - **Purpose**: Rounds a number up to the nearest integer.
   - **Syntax**: `CEIL(number)`
   - **Example**:
     ```sql
     SELECT CEIL(123.45) AS CeilValue;
     ```
     **Result**: `124`

### 6. **`FLOOR()`**
   - **Purpose**: Rounds a number down to the nearest integer.
   - **Syntax**: `FLOOR(number)`
   - **Example**:
     ```sql
     SELECT FLOOR(123.45) AS FloorValue;
     ```
     **Result**: `123`
     ## **Date Functions**
     Date functions in SQL are used to manipulate and perform operations on date and time data types. Below are some commonly used **Date Functions** along with their syntax and examples:

### 1. **SYSDATE**
   - **Purpose**: Returns the current system date and time.
   - **Syntax**:
     ```sql
     SYSDATE
     ```
   - **Example**:
     ```sql
     SELECT SYSDATE FROM dual;
     ```
     This query returns the current date and time based on the system's clock.

### 2. **CURRENT_DATE**
   - **Purpose**: Returns the current date and time based on the database's time zone.
   - **Syntax**:
     ```sql
     CURRENT_DATE
     ```
   - **Example**:
     ```sql
     SELECT CURRENT_DATE FROM dual;
     ```
     This query returns the current date and time in the time zone of the database server.

### 3. **ADD_MONTHS**
   - **Purpose**: Adds or subtracts a specified number of months to/from a date.
   - **Syntax**:
     ```sql
     ADD_MONTHS(date, number_of_months)
     ```
   - **Example**:
     ```sql
     SELECT ADD_MONTHS('2024-01-15', 3) FROM dual;
     ```
     This query adds 3 months to the given date and returns `'2024-04-15'`.

### 4. **MONTHS_BETWEEN**
   - **Purpose**: Returns the number of months between two dates.
   - **Syntax**:
     ```sql
     MONTHS_BETWEEN(date1, date2)
     ```
   - **Example**:
     ```sql
     SELECT MONTHS_BETWEEN('2024-12-01', '2024-01-01') FROM dual;
     ```
     This query returns `11`, which is the number of months between January 1, 2024, and December 1, 2024.

### 5. **NEXT_DAY**
   - **Purpose**: Returns the next date of the specified weekday after a given date.
   - **Syntax**:
     ```sql
     NEXT_DAY(date, weekday)
     ```
   - **Example**:
     ```sql
     SELECT NEXT_DAY('2024-11-07', 'MONDAY') FROM dual;
     ```
     This query returns `'2024-11-11'`, which is the next Monday after November 7, 2024.

### 6. **LAST_DAY**
   - **Purpose**: Returns the last day of the month for the specified date.
   - **Syntax**:
     ```sql
     LAST_DAY(date)
     ```
   - **Example**:
     ```sql
     SELECT LAST_DAY('2024-11-07') FROM dual;
     ```
     This query returns `'2024-11-30'`, which is the last day of November 2024.

### 7. **TO_CHAR**
   - **Purpose**: Converts a date to a string in a specified format.
   - **Syntax**:
     ```sql
     TO_CHAR(date, format)
     ```
   - **Example**:
     ```sql
     SELECT TO_CHAR(SYSDATE, 'YYYY-MM-DD HH24:MI:SS') FROM dual;
     ```
     This query converts the current date and time to a string in the format `YYYY-MM-DD HH24:MI:SS`.

### 8. **TO_DATE**
   - **Purpose**: Converts a string to a date based on the specified format.
   - **Syntax**:
     ```sql
     TO_DATE(string, format)
     ```
   - **Example**:
     ```sql
     SELECT TO_DATE('2024-11-07', 'YYYY-MM-DD') FROM dual;
     ```
     This query converts the string `'2024-11-07'` into a date value.

### 9. **EXTRACT**
   - **Purpose**: Extracts a specific part (like year, month, day, etc.) from a date.
   - **Syntax**:
     ```sql
     EXTRACT(part FROM date)
     ```
   - **Example**:
     ```sql
     SELECT EXTRACT(YEAR FROM SYSDATE) FROM dual;
     ```
     This query returns the current year.

### 10. **TRUNC**
   - **Purpose**: Truncates the date to a specified unit (e.g., day, month, year).
   - **Syntax**:
     ```sql
     TRUNC(date, format)
     ```
   - **Example**:
     ```sql
     SELECT TRUNC(SYSDATE, 'MM') FROM dual;
     ```
     This query truncates the current date to the first day of the current month.

### Summary of Date Functions in SQL:
- **SYSDATE**: Current system date and time.
- **CURRENT_DATE**: Current date and time based on database time zone.
- **ADD_MONTHS**: Add or subtract months from a date.
- **MONTHS_BETWEEN**: Number of months between two dates.
- **NEXT_DAY**: Next specified weekday after a given date.
- **LAST_DAY**: Last day of the month for a given date.
- **TO_CHAR**: Convert a date to a string in a specified format.
- **TO_DATE**: Convert a string to a date in a specified format.
- **EXTRACT**: Extract a specific part of a date.
- **TRUNC**: Truncate a date to a specified unit.

## **Conversion Functions**
Conversion functions in SQL are used to convert data from one data type to another. Here are the commonly used conversion functions with syntax and examples:

### 1. **`TO_CHAR()`**
   - **Purpose:** Converts a date, number, or other data types into a string format.
   - **Syntax:**
     ```sql
     TO_CHAR(expression, format)
     ```
   - **Example (Converting Date to String):**
     ```sql
     SELECT TO_CHAR(SYSDATE, 'DD-Mon-YYYY') AS current_date
     FROM dual;
     ```
     **Output:**
     ```
     CURRENT_DATE
     --------------
     07-Nov-2024
     ```

   - **Example (Converting Number to String):**
     ```sql
     SELECT TO_CHAR(123456.789, '999,999.99') AS formatted_number
     FROM dual;
     ```
     **Output:**
     ```
     FORMATTED_NUMBER
     -----------------
     123,456.79
     ```

---

### 2. **`TO_NUMBER()`**
   - **Purpose:** Converts a string or other data type to a numeric value.
   - **Syntax:**
     ```sql
     TO_NUMBER(expression, format)
     ```
   - **Example (Converting String to Number):**
     ```sql
     SELECT TO_NUMBER('12345.67', '99999.99') AS converted_number
     FROM dual;
     ```
     **Output:**
     ```
     CONVERTED_NUMBER
     -----------------
     12345.67
     ```

   - **Example (Converting Date to Number):**
     ```sql
     SELECT TO_NUMBER(TO_CHAR(SYSDATE, 'YYYYMMDD')) AS date_in_number
     FROM dual;
     ```
     **Output:**
     ```
     DATE_IN_NUMBER
     ---------------
     20241107
     ```

---

### 3. **`TO_DATE()`**
   - **Purpose:** Converts a string to a date format.
   - **Syntax:**
     ```sql
     TO_DATE(expression, format)
     ```
   - **Example (Converting String to Date):**
     ```sql
     SELECT TO_DATE('07-Nov-2024', 'DD-Mon-YYYY') AS converted_date
     FROM dual;
     ```
     **Output:**
     ```
     CONVERTED_DATE
     ---------------
     07-NOV-24
     ```

   - **Example (Converting Date to a Different Format):**
     ```sql
     SELECT TO_DATE('20241107', 'YYYYMMDD') AS formatted_date
     FROM dual;
     ```
     **Output:**
     ```
     FORMATTED_DATE
     ---------------
     07-NOV-24
     ```

---

### 4. **`CAST()`**
   - **Purpose:** Converts one data type to another, such as converting a string to a date or number.
   - **Syntax:**
     ```sql
     CAST(expression AS target_data_type)
     ```
   - **Example (Converting String to Date):**
     ```sql
     SELECT CAST('2024-11-07' AS DATE) AS date_value
     FROM dual;
     ```
     **Output:**
     ```
     DATE_VALUE
     -----------
     07-NOV-24
     ```

   - **Example (Converting Number to Integer):**
     ```sql
     SELECT CAST('12345.67' AS INTEGER) AS integer_value
     FROM dual;
     ```
     **Output:**
     ```
     INTEGER_VALUE
     --------------
     12345
     ```

---
## **Miscellaneous Functions:**
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

