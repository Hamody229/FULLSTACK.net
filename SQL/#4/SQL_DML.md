### **DML (Data Manipulation Language)**

It’s the set of SQL commands used to **work with the data inside tables** (not the structure).

### The main **DML commands** are:

1. **INSERT** → add new records (rows) into a table.

   ```sql
   INSERT INTO Students (ID, Name, Age)
   VALUES (1, 'Ahmed', 20);
   ```

2. **UPDATE** → modify existing records in a table.

   ```sql
   UPDATE Students
   SET Age = 21
   WHERE ID = 1;
   ```

3. **DELETE** → remove records from a table.

   ```sql
   DELETE FROM Students
   WHERE ID = 1;
   ```

4. **SELECT** (sometimes counted as DML, sometimes as separate **DRL – Data Retrieval Language**) → retrieve data from a table.

   ```sql
   SELECT Name, Age
   FROM Students
   WHERE Age > 18;
   ```

---

**Quick difference**:

* **DDL** (like `CREATE`, `ALTER`) → changes **structure/schema**.
* **DML** (like `INSERT`, `UPDATE`, `DELETE`, `SELECT`) → changes or retrieves **data inside** the structure.

____
### **`Copy data from table`**
In SQL, you can use **`INSERT … SELECT`** to insert rows into a table **from the result of a query** instead of writing values manually.

---

### Syntax:

```sql
INSERT INTO target_table (column1, column2, ...)
SELECT column1, column2, ...
FROM source_table
WHERE condition;
```

---

### Example:

Suppose you have two tables:

**Students\_2024**

| ID | Name  | Age |
| -- | ----- | --- |
| 1  | Ahmed | 20  |
| 2  | Sara  | 22  |

**Students\_Backup** (empty table with same structure).

You can copy data like this:

```sql
INSERT INTO Students_Backup (ID, Name, Age)
SELECT ID, Name, Age
FROM Students_2024
WHERE Age > 20;
```

This will insert **only students older than 20** into `Students_Backup`.



* `INSERT ... VALUES` → used when **you provide fixed values**.
* `INSERT ... SELECT` → used when **you want to insert data from another query/table**.

