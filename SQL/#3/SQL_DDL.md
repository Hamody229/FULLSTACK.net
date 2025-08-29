## `CREATE TABLE`

Used to define a new table with its **columns** and **constraints**.

```sql
CREATE TABLE Employees (
    EmpID INT PRIMARY KEY,                  -- Primary Key constraint
    FirstName VARCHAR(50) NOT NULL,         -- NOT NULL constraint
    LastName VARCHAR(50) NOT NULL,
    Email VARCHAR(100) UNIQUE,              -- UNIQUE constraint
    Salary DECIMAL(10,2) CHECK (Salary > 0),-- CHECK constraint
    DeptID INT,
    HireDate DATE DEFAULT GETDATE(),        -- DEFAULT constraint
    FOREIGN KEY (DeptID) REFERENCES Departments(DeptID) -- Foreign Key constraint
);
```

---

## Types of Constraints in `CREATE`

1. **PRIMARY KEY**

   * Ensures each row is uniquely identified.
   * Only one per table.

   ```sql
   EmpID INT PRIMARY KEY
   ```

2. **FOREIGN KEY**

   * Creates a relationship between two tables.

   ```sql
   FOREIGN KEY (DeptID) REFERENCES Departments(DeptID)
   ```

3. **UNIQUE**

   * Ensures all values in a column are different.

   ```sql
   Email VARCHAR(100) UNIQUE
   ```

4. **NOT NULL**

   * Prevents NULL values.

   ```sql
   FirstName VARCHAR(50) NOT NULL
   ```

5. **CHECK**

   * Ensures values meet a condition.

   ```sql
   Salary DECIMAL(10,2) CHECK (Salary > 0)
   ```

6. **DEFAULT**

   * Assigns a default value if none is provided.

   ```sql
   HireDate DATE DEFAULT GETDATE()
   ```

---

## Other `CREATE` Examples

* **Create a Database**

  ```sql
  CREATE DATABASE HR_Database;
  ```

* **Create a View**

  ```sql
  CREATE VIEW HighEarners AS
  SELECT FirstName, Salary
  FROM Employees
  WHERE Salary > 10000;
  ```

* **Create a Stored Procedure**

  ```sql
  CREATE PROCEDURE GetHighEarners
  AS
  BEGIN
      SELECT FirstName, Salary
      FROM Employees
      WHERE Salary > 10000;
  END;
  ```

* **Create an Index**

  ```sql
  CREATE INDEX idx_salary ON Employees(Salary);
  ```

---

The **`ALTER`** command in SQL is part of DDL.
It’s used to **modify the structure of an existing table** (not the data).

### Common uses of `ALTER`:

1. **Add a new column**

   ```sql
   ALTER TABLE Students ADD Email VARCHAR(100);
   ```

2. **Modify a column’s datatype/size**

   ```sql
   ALTER TABLE Students MODIFY Age SMALLINT;
   ```

3. **Rename a column** (syntax depends on the SQL dialect)

   ```sql
   -- MySQL
   ALTER TABLE Students RENAME COLUMN Name TO FullName;

   -- SQL Server
   EXEC sp_rename 'Students.Name', 'FullName', 'COLUMN';
   ```

4. **Drop (delete) a column**

   ```sql
   ALTER TABLE Students DROP COLUMN Email;
   ```

5. **Rename the table itself**

   ```sql
   ALTER TABLE Students RENAME TO Learners;
   ```



