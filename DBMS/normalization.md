# Normalization

## Table of Contents
1. [Normalization](#normalization)
    - [Need for Normalization](#need-for-normalization)
    - [Anomalies in DBMS](#anomalies-in-dbms)
    - [First Normal Form (1NF)](#first-normal-form-1nf)
    - [Second Normal Form (2NF)](#second-normal-form-2nf)
    - [Third Normal Form (3NF)](#third-normal-form-3nf)
    - [Boyce-Codd Normal Form (BCNF)](#boyce-codd-normal-form-bcnf)
2. [Advantages of Normalization](#advantages-of-normalization)
3. [Disadvantages of Normalization](#disadvantages-of-normalization)
4. [Database Normalization Rules](#database-normalization-rules)
5. [Examples](#examples)

## Normalization

### Need for Normalization
Normalization is a database schema design technique that minimizes redundancy and dependency by splitting large tables into smaller ones and defining relationships between them. It improves clarity in organizing data.

Some key points about normalization:
- Refers to the structure of a database.
- Developed by IBM researcher E.F. Codd in the 1970s.
- Increases the clarity in organizing data in a database.

### Anomalies in DBMS
There are three types of anomalies that occur when the database is not normalized:
1. **Insertion Anomaly**: Inability to insert data due to constraints.
2. **Update Anomaly**: Data inconsistency when updating records.
3. **Deletion Anomaly**: Loss of useful data when deleting records.

### First Normal Form (1NF)
A table is in 1NF if:
- Each table cell contains a single value.
- Each record is unique.

**Example:**

Sample Employee Table (not in 1NF):

| Employee | Age | Department          |
|----------|-----|---------------------|
| Melvin   | 32  | Marketing, Sales    |
| Edward   | 45  | Quality Assurance   |
| Alex     | 36  | Human Resource      |

Employee Table in 1NF:

| Employee | Age | Department        |
|----------|-----|-------------------|
| Melvin   | 32  | Marketing         |
| Melvin   | 32  | Sales             |
| Edward   | 45  | Quality Assurance |
| Alex     | 36  | Human Resource    |

### Second Normal Form (2NF)
A table is in 2NF if:
- It is in 1NF.
- It has no Partial Dependency (no non-prime attribute depends on a part of a candidate key).

**Example:**

Employee Table (in 1NF):

| Emp_Id | Emp_Name | Dept_Id | Dept_Name        |
|--------|----------|---------|------------------|
| 100    | Rock     | 10      | IT               |
| 101    | Sam      | 20      | HR               |
| 102    | John     | 30      | Finance          |
| 103    | Alice    | 40      | Admin            |

To convert to 2NF, split into two tables:

Employee:

| Emp_Id | Emp_Name |
|--------|----------|
| 100    | Rock     |
| 101    | Sam      |
| 102    | John     |
| 103    | Alice    |

Department:

| Dept_Id | Dept_Name |
|---------|-----------|
| 10      | IT        |
| 20      | HR        |
| 30      | Finance   |
| 40      | Admin     |

### Third Normal Form (3NF)
A table is in 3NF if:
- It is in 2NF.
- No non-prime attribute is transitively dependent on the primary key.

**Example:**

Employee Table (in 2NF):

| Emp_Id | Emp_Name | Dept_Id | Dept_Name | ZIP  | City    |
|--------|----------|---------|-----------|------|---------|
| 100    | Rock     | 10      | IT        | 12345| New York|
| 101    | Sam      | 20      | HR        | 23456| Boston  |
| 102    | John     | 30      | Finance   | 34567| Chicago |
| 103    | Alice    | 40      | Admin     | 45678| Houston |

To convert to 3NF, split into two tables:

Employee:

| Emp_Id | Emp_Name | Dept_Id |
|--------|----------|---------|
| 100    | Rock     | 10      |
| 101    | Sam      | 20      |
| 102    | John     | 30      |
| 103    | Alice    | 40      |

Department:

| Dept_Id | Dept_Name |
|---------|-----------|
| 10      | IT        |
| 20      | HR        |
| 30      | Finance   |
| 40      | Admin     |

ZIP_City:

| ZIP  | City    |
|------|---------|
| 12345| New York|
| 23456| Boston  |
| 34567| Chicago |
| 45678| Houston |

### Boyce-Codd Normal Form (BCNF)
A table is in BCNF if:
- It is in 3NF.
- For each functional dependency (X → Y), X is a super key.

**Example:**

Consider the table:

| Course | Instructor | Room  |
|--------|------------|-------|
| Math   | John       | 101   |
| Science| Alice      | 102   |
| Math   | Alice      | 101   |
| Science| John       | 102   |

To convert to BCNF, split into two tables:

Course_Instructor:

| Course | Instructor |
|--------|------------|
| Math   | John       |
| Science| Alice      |
| Math   | Alice      |
| Science| John       |

Instructor_Room:

| Instructor | Room  |
|------------|-------|
| John       | 101   |
| Alice      | 102   |

## Advantages of Normalization
1. Reduces duplicate data and overall database size.
2. Improves performance by making data access faster.
3. Allows for narrower tables with more data records per page.
4. Ensures faster maintenance tasks.
5. Facilitates joining only the needed tables.

## Disadvantages of Normalization
1. Requires more table joins, making tasks more tedious.
2. Stores repeated data as codes, necessitating lookup tables.
3. Makes the data model complex and harder to query against.
4. Slows down performance as normalization level increases.
5. Requires proper knowledge to execute efficiently.

## Database Normalization Rules
### First Normal Form (1NF)
- Each table cell contains a single value.
- Each record is unique.

### Second Normal Form (2NF)
- Table is in 1NF.
- No Partial Dependency exists.

### Third Normal Form (3NF)
- Table is in 2NF.
- No transitive dependency exists.

### Boyce-Codd Normal Form (BCNF)
- Table is in 3NF.
- For each functional dependency (X → Y), X is a super key.

## Examples
### First Normal Form (1NF)
**Before:**

| Employee | Age | Department          |
|----------|-----|---------------------|
| Melvin   | 32  | Marketing, Sales    |
| Edward   | 45  | Quality Assurance   |
| Alex     | 36  | Human Resource      |

**After:**

| Employee | Age | Department        |
|----------|-----|-------------------|
| Melvin   | 32  | Marketing         |
| Melvin   | 32  | Sales             |
| Edward   | 45  | Quality Assurance |
| Alex     | 36  | Human Resource    |

### Second Normal Form (2NF)
**Before:**

| Emp_Id | Emp_Name | Dept_Id | Dept_Name        |
|--------|----------|---------|------------------|
| 100    | Rock     | 10      | IT               |
| 101    | Sam      | 20      | HR               |
| 102    | John     | 30      | Finance          |
| 103    | Alice    | 40      | Admin            |

**After:**

Employee:

| Emp_Id | Emp_Name |
|--------|----------|
| 100    | Rock     |
| 101    | Sam      |
| 102    | John     |
| 103    | Alice    |

Department:

| Dept_Id | Dept_Name |
|---------|-----------|
| 10      | IT        |
| 20      | HR        |
| 30      | Finance   |
| 40      | Admin     |

### Third Normal Form (3NF)
**Before:**

| Emp_Id | Emp_Name | Dept_Id | Dept_Name | ZIP  | City    |
|--------|----------|---------|-----------|------|---------|
| 100    | Rock     | 10      | IT        | 12345| New York|
| 101    | Sam      | 20      | HR        | 23456| Boston  |
| 102    | John     | 30      | Finance   | 34567| Chicago |
| 103    | Alice    | 40      | Admin     | 45678| Houston |

**After:**

Employee:

| Emp_Id | Emp_Name | Dept_Id |
|--------|----------|---------|
| 100    | Rock     | 10      |
| 101    | Sam      | 20      |
| 102    | John     | 30      |
| 103    | Alice    | 40      |

Department:

| Dept_Id | Dept_Name |
|---------|-----------|
| 10      | IT        |
| 20      | HR        |
| 30      | Finance   |
| 40      | Admin     |

ZIP_City:

| ZIP  | City    |
|------|---------|
| 12345| New York|
| 23456| Boston  |
| 34567| Chicago |
| 45678| Houston |

### Boyce-Codd Normal Form (BCNF)
**Before:**

| Course | Instructor | Room  |
|--------|------------|-------|
| Math   | John       | 101   |
| Science| Alice      | 102   |
| Math   | Alice      | 101   |
| Science| John       | 102   |

**After:**

Course_Instructor:

| Course | Instructor |
|--------|------------|
| Math   | John       |
| Science| Alice      |
| Math   | Alice      |
| Science| John       |

Instructor_Room:

| Instructor | Room  |
|------------|-------|
| John       | 101   |
| Alice      | 102   |
