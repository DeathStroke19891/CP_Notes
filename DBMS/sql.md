# Table of Contents

1. [SQL](#sql)
2. [RDBMS: Relational Database Management System](#rdbms-relational-database-management-system)
3. [SQL Data Types](#sql-data-types)
4. [Types of SQL Commands](#types-of-sql-commands)
5. [SQL Queries](#sql-queries)
6. [Conclusion](#conclusion)

---

## SQL

SQL: Structured Query Language, used to access and manipulate data.
SQL used CRUD operations to communicate with DB.

1. CREATE - execute INSERT statements to insert new tuple into the relation.
2. READ - Read data already in the relations.
3. UPDATE - Modify already inserted data in the relation.
4. DELETE - Delete specific data point/tuple/row or multiple rows.

SQL is not DB, is a query language.

## What is RDBMS? (Relational Database Management System)

1. Software that enables us to implement designed relational model.
2. e.g., MySQL, MS SQL, Oracle, IBM etc.
3. Table/Relation is the simplest form of data storage object in R-DB.
4. MySQL is open-source RDBMS, and it uses SQL for all CRUD operations.
5. MySQL uses a client-server model, where the client is CLI or frontend that uses services provided by the MySQL server.

### Difference between SQL and MySQL

SQL is Structured Query language used to perform CRUD operations in R-DB, while MySQL is an RDBMS used to store, manage, and administrate DB (provided by itself) using SQL.

---

## SQL Data Types

In SQL DB, data is stored in the form of tables. Data can be of different types, like INT, CHAR etc.

| S.No | Data Type  | Description                                                         |
| ---- | ---------- | ------------------------------------------------------------------- |
| 1    | CHAR       | Fixed-length string, maximum length up to 255 characters.           |
| 2    | VARCHAR    | Variable-length string, maximum length up to 65535 characters.      |
| 3    | TINYTEXT   | String with a maximum length of 255 characters.                     |
| 4    | TEXT       | String with a maximum length of 65535 characters.                   |
| 5    | MEDIUMTEXT | String with a maximum length of 16777215 characters.                |
| 6    | MEDIUMBLOB | Binary large object with a maximum length of 16777215 characters.   |
| 7    | LONGTEXT   | String with a maximum length of 4294967295 characters.              |
| 8    | LONGBLOB   | Binary large object with a maximum length of 4294967295 characters. |
| 9    | TINYINT    | Integer, range from -128 to 127.                                    |
| 10   | SMALLINT   | Integer, range from -32768 to 32767.                                |
| 11   | MEDIUMINT  | Integer, range from -8388608 to 8388607.                            |
| 12   | INT        | Integer, range from -2147483648 to 2147483647.                      |
| 13   | BIGINT     | Integer, range from -9223372036854775808 to 9223372036854775807.    |
| 14   | FLOAT      | Decimal with precision to 23 digits.                                |
| 15   | DOUBLE     | Decimal with 24 to 53 digits.                                       |
| 16   | DECIMAL    | Double stored as a string.                                          |
| 17   | DATE       | YYYY-MM-DD format                                                   |
| 18   | DATETIME   | YYYY-MM-DD HH:MM:SS format                                          |
| 19   | TIMESTAMP  | YYYYMMDDHHMMSS format                                               |
| 20   | TIME       | HH:MM:SS format                                                     |
| 21   | ENUM       | One of the preset values.                                           |
| 22   | SET        | One or many of the preset values.                                   |
| 23   | BOOLEAN    | 0/1                                                                 |
| 24   | BIT        | Stores values in bits, e.g., BIT(n) up to 64.                       |

---

## Types of SQL Commands

### DDL (Data Definition Language)

Defines relation schema.

1. CREATE: create table, DB, view.
2. ALTER TABLE: modification in table structure, e.g., change column datatype or add/remove columns.
3. DROP: delete table, DB, view.
4. TRUNCATE: remove all the tuples from the table.
5. RENAME: rename DB name, table name, column name etc.

### DRL/DQL (Data Retrieval Language / Data Query Language)

Retrieves data from the tables.

1. SELECT: retrieve specific columns from one or more tables.

### DML (Data Manipulation Language)

Modifies data in the tables.

1. INSERT: insert data into a relation.
2. UPDATE: update relation data.
3. DELETE: delete row(s) from the relation.

### DCL (Data Control Language)

Manages user access rights.

1. GRANT: access privileges to the DB.
2. REVOKE: revoke user access privileges.

### TCL (Transaction Control Language)

Manages transactions in the DB.

1. START TRANSACTION: begin a transaction.
2. COMMIT: apply all the changes and end transaction.
3. ROLLBACK: discard changes and end transaction.
4. SAVEPOINT: set a checkpoint within a transaction.

---

## SQL Queries

```sql
-- CREATE DATABASE
CREATE DATABASE IF NOT EXISTS db_name;
Usage of DB
  
 
-- USE DB
USE db_name;
Dropping DB
  
 
-- DROP DATABASE
DROP DATABASE IF EXISTS db_name;
Listing DBs and Tables
  
 
-- SHOW DATABASES
SHOW DATABASES;

-- SHOW TABLES
SHOW TABLES;
Data Retrieval Language (DRL)
SELECT Statement
  
 
-- Basic SELECT statement
SELECT * FROM table_name;

-- Select specific columns
SELECT column1, column2 FROM table_name;

-- Select with WHERE clause
SELECT * FROM customers WHERE age > 18;

-- Select with ORDER BY clause
SELECT * FROM customers ORDER BY name ASC;

-- Select with GROUP BY clause
SELECT city, COUNT(*) FROM customers GROUP BY city;
Filtering and Sorting
  
 
-- WHERE clause
SELECT * FROM customers WHERE age BETWEEN 20 AND 30;

-- ORDER BY clause
SELECT * FROM customers ORDER BY age DESC;

-- GROUP BY clause
SELECT city, COUNT(*) FROM customers GROUP BY city HAVING COUNT(*) > 5;
Joins
  
 
-- INNER JOIN
SELECT * FROM orders INNER JOIN customers ON orders.customer_id = customers.id;

-- LEFT JOIN
SELECT * FROM customers LEFT JOIN orders ON customers.id = orders.customer_id;

-- RIGHT JOIN
SELECT * FROM orders RIGHT JOIN customers ON orders.customer_id = customers.id;

-- FULL JOIN
SELECT * FROM customers FULL JOIN orders ON customers.id = orders.customer_id;
Constraints (DDL)
Primary Key
  
 
-- Define Primary Key
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    department VARCHAR(50)
);
Foreign Key
  
 
-- Define Foreign Key
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    order_date DATE,
    customer_id INT,
    FOREIGN KEY (customer_id) REFERENCES customers(id)
);
Unique Constraint
  
 
-- Unique Constraint
CREATE TABLE customers (
    id INT PRIMARY KEY,
    email VARCHAR(255) UNIQUE,
    phone VARCHAR(20)
);
Check Constraint
  
 
-- Check Constraint
CREATE TABLE employees (
    id INT PRIMARY KEY,
    age INT CHECK (age >= 18),
    department VARCHAR(50)
);
Default Constraint
  
 
-- Default Constraint
CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    batch_year INT DEFAULT 2023
);
Data Manipulation Language (DML)
INSERT Statement
  
 
-- Basic INSERT statement
INSERT INTO customers (name, email) VALUES ('Alice', 'alice@example.com');

-- Insert multiple rows
INSERT INTO customers (name, email)
VALUES ('Bob', 'bob@example.com'),
       ('Charlie', 'charlie@example.com');
UPDATE Statement
  
 
-- Basic UPDATE statement
UPDATE customers SET email = 'alice_new@example.com' WHERE name = 'Alice';
DELETE Statement
   
 
-- Basic DELETE statement
DELETE FROM customers WHERE name = 'Alice';

-- Delete all rows
DELETE FROM customers;
Joining Tables
INNER JOIN
   
 
-- INNER JOIN
SELECT * FROM orders INNER JOIN customers ON orders.customer_id = customers.id;
LEFT JOIN
   
 
-- LEFT JOIN
SELECT * FROM customers LEFT JOIN orders ON customers.id = orders.customer_id;
RIGHT JOIN
   
 
-- RIGHT JOIN
SELECT * FROM orders RIGHT JOIN customers ON orders.customer_id = customers.id;
FULL JOIN
   
 
-- FULL JOIN
SELECT * FROM customers FULL JOIN orders ON customers.id = orders.customer_id;
Set Operations
UNION
   
 
-- UNION
SELECT * FROM table1
UNION
SELECT * FROM table2;
INTERSECT
   
 
-- INTERSECT
SELECT * FROM table1
INTERSECT
SELECT * FROM table2;
EXCEPT
   
 
-- EXCEPT
SELECT * FROM table1
EXCEPT
SELECT * FROM table2;
Subqueries
   
 
-- Subquery in SELECT statement
SELECT name, (SELECT COUNT(*) FROM orders WHERE orders.customer_id = customers.id) AS order_count
FROM customers;

-- Subquery in WHERE clause
SELECT * FROM customers
WHERE id IN (SELECT customer_id FROM orders);

-- Subquery in FROM clause
SELECT * FROM (SELECT * FROM orders WHERE order_date > '2023-01-01') AS recent_orders;
MySQL Views
Creating Views
  
 
-- Create a view
CREATE VIEW customer_orders AS
SELECT customers.name, orders.order_id
FROM customers
JOIN orders ON customers.id = orders.customer_id;
Using Views
  
 
-- Query from view
SELECT * FROM customer_orders;

-- Update view
CREATE OR REPLACE VIEW customer_orders AS
SELECT customers.name, orders.order_id, orders.total_amount
FROM customers
JOIN orders ON customers.id = orders.customer_id;
Dropping Views
  
 
-- Drop a view
DROP VIEW IF EXISTS customer_orders;
```

# Conclusion

SQL is a powerful language for managing and manipulating relational databases. Understanding its various commands and constructs enables efficient data retrieval, manipulation, and management. Whether working with small-scale databases or large enterprise systems, SQL remains fundamental in interacting with data effectively.
