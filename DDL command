Here are the detailed examples of all the **ALTER** command variations that can be used in SQL:

### 1. **Add Column**
   - **Definition**: Adds a new column to an existing table.
   - **Syntax**:
     ```sql
     ALTER TABLE table_name
     ADD column_name datatype;
     ```
   - **Example**:
     ```sql
     ALTER TABLE Employee
     ADD Salary DECIMAL(10, 2);
     ```
     This will add a new column `Salary` of type `DECIMAL(10, 2)` to the `Employee` table.

### 2. **Modify Column**
   - **Definition**: Modifies the data type or other attributes of an existing column.
   - **Syntax**:
     ```sql
     ALTER TABLE table_name
     MODIFY column_name new_datatype;
     ```
   - **Example**:
     ```sql
     ALTER TABLE Employee
     MODIFY Age INT NOT NULL;
     ```
     This will modify the `Age` column in the `Employee` table to be of type `INT` and set it to `NOT NULL`.

### 3. **Rename Column**
   - **Definition**: Renames an existing column in the table.
   - **Syntax**:
     ```sql
     ALTER TABLE table_name
     RENAME COLUMN old_column_name TO new_column_name;
     ```
   - **Example**:
     ```sql
     ALTER TABLE Employee
     RENAME COLUMN Age TO Employee_Age;
     ```
     This will rename the column `Age` to `Employee_Age` in the `Employee` table.

### 4. **Add Constraints**
   - **Definition**: Adds a new constraint (like `PRIMARY KEY`, `FOREIGN KEY`, etc.) to an existing table.
   - **Syntax**:
     ```sql
     ALTER TABLE table_name
     ADD CONSTRAINT constraint_name constraint_type (column_name);
     ```
   - **Example**:
     ```sql
     ALTER TABLE Employee
     ADD CONSTRAINT pk_employee_id PRIMARY KEY (ID);
     ```
     This will add a `PRIMARY KEY` constraint on the `ID` column of the `Employee` table.

### 5. **Drop Column**
   - **Definition**: Removes an existing column from the table.
   - **Syntax**:
     ```sql
     ALTER TABLE table_name
     DROP COLUMN column_name;
     ```
   - **Example**:
     ```sql
     ALTER TABLE Employee
     DROP COLUMN Salary;
     ```
     This will remove the `Salary` column from the `Employee` table.

### 6. **Drop Constraint**
   - **Definition**: Removes an existing constraint from a table (like `PRIMARY KEY`, `FOREIGN KEY`, etc.).
   - **Syntax**:
     ```sql
     ALTER TABLE table_name
     DROP CONSTRAINT constraint_name;
     ```
   - **Example**:
     ```sql
     ALTER TABLE Employee
     DROP CONSTRAINT pk_employee_id;
     ```
     This will drop the `PRIMARY KEY` constraint from the `ID` column of the `Employee` table.

### 7. **Change Table Name**
   - **Definition**: Changes the name of an existing table.
   - **Syntax**:
     ```sql
     ALTER TABLE old_table_name
     RENAME TO new_table_name;
     ```
   - **Example**:
     ```sql
     ALTER TABLE Employee
     RENAME TO Staff;
     ```
     This will rename the `Employee` table to `Staff`.

### 8. **Modify Default Value of a Column**
   - **Definition**: Changes the default value for a column in an existing table.
   - **Syntax**:
     ```sql
     ALTER TABLE table_name
     MODIFY column_name SET DEFAULT default_value;
     ```
   - **Example**:
     ```sql
     ALTER TABLE Employee
     MODIFY Status SET DEFAULT 'Active';
     ```
     This sets the default value for the `Status` column in the `Employee` table to `'Active'`.

### Summary of **ALTER** Command:

- **ADD**: Add new columns or constraints.
- **MODIFY**: Modify existing columns (datatype or constraints).
- **RENAME**: Rename columns or tables.
- **DROP**: Remove columns or constraints.
- **SET DEFAULT**: Change the default value of a column.

These **ALTER** command variations are essential for managing and evolving the structure of a database after its creation.
