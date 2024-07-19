# Database Concepts and Terminologies

## Table of Contents
1. [Relation](#relation)
2. [Attributes](#attributes)
3. [Tuple](#tuple)
4. [Domain](#domain)
5. [Degree of a Table](#degree-of-a-table)
6. [Extension and Intension of a Relation](#extension-and-intension-of-a-relation)
7. [Cardinality](#cardinality)
8. [NULL](#null)
9. [Relational Database](#relational-database)
10. [Attributes - Types of Attributes](#attributes-types-of-attributes)
11. [Mapping Cardinalities](#mapping-cardinalities)
12. [Keys](#keys)
    - [Superkey](#superkey)
    - [Candidate Key](#candidate-key)
    - [Primary Key](#primary-key)
    - [Alternate Key](#alternate-key)
    - [Composite Key](#composite-key)
    - [Secondary Key](#secondary-key)
    - [Foreign Key](#foreign-key)
13. [Database Schema](#database-schema)
14. [Relational Schema Diagram Notation](#relational-schema-diagram-notation)
15. [The Entity-Relationship Model](#the-entity-relationship-model)
    - [Entity](#entity)
    - [Entity Sets](#entity-sets)
    - [Attributes](#attributes-er)
    - [Relationship Sets](#relationship-sets)

## Relation
A relation is defined as a table with columns and rows. According to E.F. Codd, data can be stored in the form of a two-dimensional (2D) table. Each row represents a record, and each column represents an attribute.

Example:
| StudentID | Name | Age |
|-----------|------|-----|
| 1         | John | 20  |
| 2         | Jane | 22  |

## Attributes
Attributes are named columns of a relation. They hold the information about the objects and represent the entire database. The order of attributes does not affect the meaning of the database.

Example:
| **StudentID** | **Name** | **Age** |
|---------------|----------|---------|
| 1             | John     | 20      |
| 2             | Jane     | 22      |

## Tuple
A tuple is a single row of a relation (table). A tuple with 'n' attributes is called an n-tuple.

Example:
| **StudentID** | **Name** | **Age** |
|---------------|----------|---------|
| **1**         | **John** | **20**  |

## Domain
The domain of an attribute contains the set of values that the attribute may assume. 

Example:
- Domain of `Die`: {1, 2, 3, 4, 5, 6}
- Domain of `Coin`: {Head, Tail}

## Degree of a Table
The degree of a table is the number of attributes (columns) in a table.

Example:
| **StudentID** | **Name** | **Age** |
|---------------|----------|---------|
Degree: 3

## Extension and Intension of a Relation
- **Extension**: The set of rows that appear in a relation at any given instant of time. It varies with time as rows are created, deleted, or updated.
- **Intension**: The permanent part of the table, independent of time, corresponds to what is specified in the relational schema.

## Cardinality
Cardinality is defined as the number of rows (tuples) in a table. It changes as rows are added or deleted.

## NULL
The NULL value indicates that the value does not exist or is not known. It can mean missing or not applicable.

## Relational Database
A relational database is a collection of normalized or structured relations with distinct relation names.

## Attributes - Types of Attributes
Attributes can be classified into:
1. Simple attributes
2. Composite attributes
3. Single-valued attributes
4. Multi-valued attributes
5. Derived attributes
6. Null attributes

Example:
| **StudentID** | **Name** | **Age** | **PhoneNumbers** |
|---------------|----------|---------|------------------|
| 1             | John     | 20      | 123-456, 789-012 |
| 2             | Jane     | 22      | 345-678          |

## Mapping Cardinalities
Mapping cardinalities express the number of entities to which another entity can be associated via a relationship set.
- **One to One**: An entity in A is associated with at most one entity in B.
- **One to Many**: An entity in A is associated with any number of entities in B.
- **Many to One**: An entity in A is associated with at most one entity in B.
- **Many to Many**: An entity in A is associated with any number of entities in B.

## Keys
A key is a field or group of fields (attributes) whose values are unique throughout all rows of the table.

### Superkey
A set of one or more attributes that uniquely identify a row in a table.

### Candidate Key
Minimal superkeys; no proper subset is a superkey.

### Primary Key
A candidate key chosen as the principal means of identifying tuples within a relation. It cannot contain null values.

### Alternate Key
Candidate keys that are not selected as the primary key.

### Composite Key
A primary key made up of more than one attribute.

### Secondary Key
Attributes used strictly for data retrieval purposes.

### Foreign Key
An attribute in one table that references a primary key in another table.

Example:
| **StudentID** | **Name** | **DeptID** |
|---------------|----------|------------|
| 1             | John     | 10         |
| 2             | Jane     | 20         |

| **DeptID** | **DeptName** |
|------------|--------------|
| 10         | CS           |
| 20         | EE           |

## Database Schema
The database schema is the logical design of the database, while the database instance is a snapshot of the data at a given instant in time.

## Relational Schema Diagram Notation
A relational schema can be depicted through a diagram with relations drawn as boxes and attributes listed within the boxes. Primary keys are underlined and foreign key dependencies are illustrated with arrows.

## The Entity-Relationship Model
The E-R model represents the overall logical structure of a database using entities, relationships, and attributes.

### Entity
An object that exists and is distinguishable from other objects. Represented by a set of attributes.

### Entity Sets
A set of entities of the same type that share the same properties or attributes.

Example:
| **Student Name** | **Address** | **Admission No** |
|------------------|-------------|------------------|
| Salman           | Hyderabad   | 27096-12-101     |
| Muneer           | Sec'bad     | 27096-12-102     |

### Attributes (E-R)
Classified into:
1. Simple attributes
2. Composite attributes
3. Single-valued attributes
4. Multi-valued attributes
5. Derived attributes
6. Null attributes

### Relationship Sets
A set of relationships of the same type. It is an association among several entities.

Example:
| **StudentID** | **AccountNo** |
|---------------|---------------|
| 1             | A-101         |
| 2             | A-215         |
