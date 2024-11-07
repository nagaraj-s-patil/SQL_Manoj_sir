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
