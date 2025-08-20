# SQL Commands Quick Reference Notes

## Data Definition Language (DDL)

### CREATE
Creates new database objects.

```sql
-- Create a database
CREATE DATABASE school;

-- Create a table
CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    age INT CHECK (age > 0),
    email VARCHAR(100) UNIQUE
);
```

### ALTER
Modifies existing database objects.

```sql
-- Add a column
ALTER TABLE students ADD graduation_year INT;

-- Modify column data type
ALTER TABLE students MODIFY name VARCHAR(100);

-- Drop a column
ALTER TABLE students DROP COLUMN email;
```

### DROP
Removes database objects.

```sql
-- Drop a table
DROP TABLE students;

-- Drop a database
DROP DATABASE school;
```

### TRUNCATE
Removes all records from a table, but keeps the structure.

```sql
TRUNCATE TABLE students;
```

## Data Manipulation Language (DML)

### SELECT
Retrieves data from the database.

```sql
-- Select all columns and rows
SELECT * FROM students;

-- Select specific columns
SELECT name, age FROM students;

-- Filter with WHERE
SELECT * FROM students WHERE age > 18;

-- Order results
SELECT name, age FROM students ORDER BY age DESC;

-- Group results
SELECT grade, COUNT(*) AS student_count 
FROM students 
GROUP BY grade;

-- Join tables
SELECT s.name, c.course_name
FROM students s
JOIN enrollments e ON s.id = e.student_id
JOIN courses c ON e.course_id = c.id;
```

### INSERT
Adds new records to a table.

```sql
-- Insert a single row
INSERT INTO students (id, name, age) 
VALUES (1, 'John Doe', 20);

-- Insert multiple rows
INSERT INTO students (id, name, age) VALUES
    (2, 'Jane Smith', 19),
    (3, 'Bob Johnson', 21);
```

### UPDATE
Modifies existing records.

```sql
-- Update a single column
UPDATE students SET age = 22 WHERE id = 1;

-- Update multiple columns
UPDATE students 
SET age = 20, name = 'John Smith' 
WHERE id = 1;
```

### DELETE
Removes records from a table.

```sql
-- Delete specific records
DELETE FROM students WHERE id = 3;

-- Delete all records
DELETE FROM students;
```

## Transaction Control Language (TCL)

### COMMIT
Saves transactions permanently.

```sql
BEGIN;
    UPDATE accounts SET balance = balance - 100 WHERE id = 1;
    UPDATE accounts SET balance = balance + 100 WHERE id = 2;
COMMIT;
```

### ROLLBACK
Undoes transactions that haven't been committed.

```sql
BEGIN;
    UPDATE accounts SET balance = balance - 500 WHERE id = 1;
    -- Something went wrong, undo changes
    ROLLBACK;
```

### SAVEPOINT
Creates points within a transaction to which you can roll back.

```sql
BEGIN;
    UPDATE accounts SET balance = balance - 100 WHERE id = 1;
    SAVEPOINT sp1;
    UPDATE accounts SET balance = balance + 100 WHERE id = 2;
    -- Roll back to savepoint if needed
    ROLLBACK TO sp1;
COMMIT;
```

## Common SQL Clauses & Functions

### WHERE Conditions
```sql
-- Comparison operators
SELECT * FROM products WHERE price > 100;
SELECT * FROM users WHERE status = 'active';

-- BETWEEN
SELECT * FROM orders WHERE order_date BETWEEN '2023-01-01' AND '2023-12-31';

-- IN
SELECT * FROM products WHERE category_id IN (1, 2, 3);

-- LIKE
SELECT * FROM customers WHERE name LIKE 'J%'; -- Names starting with J
SELECT * FROM products WHERE description LIKE '%wireless%'; -- Contains 'wireless'
```

### Aggregate Functions
```sql
SELECT 
    COUNT(*) AS total_students,
    AVG(age) AS average_age,
    MIN(age) AS youngest,
    MAX(age) AS oldest,
    SUM(credits) AS total_credits
FROM students;
```

### String Functions
```sql
-- Concatenate strings
SELECT CONCAT(first_name, ' ', last_name) AS full_name FROM employees;

-- Substring
SELECT SUBSTRING(description, 1, 50) AS short_desc FROM products;
```

### Date Functions
```sql
-- Current date/time
SELECT CURRENT_DATE(), CURRENT_TIMESTAMP();

-- Extract parts
SELECT EXTRACT(YEAR FROM hire_date) AS hire_year FROM employees;

-- Date arithmetic
SELECT order_date, DATE_ADD(order_date, INTERVAL 30 DAY) AS due_date FROM orders;
```

## Indexes and Views

### Indexes
```sql
-- Create an index
CREATE INDEX idx_student_name ON students(name);

-- Create a unique index
CREATE UNIQUE INDEX idx_email ON users(email);
```

### Views
```sql
-- Create a view
CREATE VIEW honor_students AS
SELECT id, name, grade 
FROM students 
WHERE grade = 'A';

-- Using a view
SELECT * FROM honor_students;
```

These notes cover the most essential SQL commands and features. Each database system (MySQL, PostgreSQL, SQL Server, etc.) may have slight syntax variations.
