# Database Management System Introduction

## Table of Contents
1. [Basic Definitions](#basic-definitions)
2. [Typical DBMS Functionality](#typical-dbms-functionality)
3. [Example of a Database (UNIVERSITY)](#example-of-a-database-university)
4. [Main Characteristics of the Database Approach](#main-characteristics-of-the-database-approach)
5. [Database Users](#database-users)
6. [Data Models](#data-models)
7. [Schemas and Instances](#schemas-and-instances)
8. [Three-schema Architecture](#three-schema-architecture)
9. [Database Languages and Interfaces](#database-languages-and-interfaces)

## Basic Definitions
- **Data**: Raw facts and figures that can be processed to obtain information.
- **Database**: A structured collection of related data that is stored electronically in a computer system.
- **DBMS (Database Management System)**: Software that allows users to interact with a database, providing functionalities for data storage, retrieval, and management.
- **Data Model**: A conceptual representation of data structures, relationships, and constraints to facilitate data organization and manipulation.

## Typical DBMS Functionality
- **Define a Database**: Specify data types, structures, and constraints for creating a database schema.
- **Construct or Load Database Contents**: Populate the database with initial data on a secondary storage medium.
- **Manipulate the Database**:
  - **Retrieval**: Querying data, generating reports based on user requirements.
  - **Modification**: Inserting, deleting, and updating data records to maintain database consistency.
  - **Access through Web Applications**: Interacting with the database via web interfaces for remote data access.
- **Processing and Sharing**:
  - Support concurrent users and application programs accessing and modifying data while ensuring data integrity and consistency.

## Example of a Database (UNIVERSITY)
- **Entities**:
  - Student, Professor, Course, Department.
- **Attributes**:
  - Student (ID, Name, GPA), Professor (ID, Name, Department), Course (Code, Title, Credits), Department (Code, Name).
- **Relationships**:
  - Student enrolls in Course, Professor teaches Course, Department offers Course.
- **Sample Queries**:
  - Retrieve all students enrolled in a specific course.
  - Find the average GPA of students in a particular department.

## Main Characteristics of the Database Approach
- **Data Abstraction**:
  - Allows program-data independence and operation independence by hiding storage details and presenting a conceptual view of the database.
- **Support of Multiple Views**:
  - Users can have different perspectives of the database, focusing on specific data of interest without being concerned with underlying storage structures.
- **Data Model Usage**:
  - Relational model provides a structured way to represent data using entities, attributes, and relationships, offering a user-friendly view of the database.
- **Program-Operation Independence**:
  - Enables changing data storage structures and operations without altering DBMS access programs, enhancing flexibility and adaptability.

## Database Users
- **Types of Database Users**:
  - **End Users**: Individuals who interact with the database through application programs or queries to retrieve or manipulate data. They include casual users, parametric users, and naive users.
  - **Application Programmers**: Users who develop applications that interact with the database, writing code to perform specific functions like data entry, retrieval, and processing.
  - **Database Administrators (DBAs)**: DBAs manage and maintain the database system, ensuring its security, performance, and integrity. They handle tasks such as backup and recovery, user access control, and schema modifications.
- **Examples**:
  - An end user accessing a university database to view course schedules.
  - An application programmer developing a student registration system.
  - A DBA configuring user permissions and optimizing database performance.

## Data Models
- **Types of Data Models**:
  - **Relational Model**: Represents data in tabular form with rows and columns, where entities are stored as tables, attributes as columns, and relationships as keys.
  - **Hierarchical Model**: Organizes data in a tree-like structure with parent-child relationships, suitable for representing one-to-many relationships.
  - **Network Model**: Extends the hierarchical model by allowing many-to-many relationships through pointers, enhancing data retrieval capabilities.
  - **Object-Oriented Model**: Represents data as objects with attributes and methods, facilitating complex data structures and inheritance.
- **Examples**:
  - In a university database, the relational model can represent students, courses, and professors as separate tables with relationships defined by keys.
  - A hierarchical model can depict organizational structures with departments as parent nodes and employees as child nodes.
  - An object-oriented model can model a library system with objects like books, authors, and patrons having attributes and behaviors.

## Schemas and Instances
- **Database Schema**:
  - Defines the structure of the database, including tables, attributes, relationships, and constraints. It provides a blueprint for organizing and storing data in the database.
- **Database Instance**:
  - Represents the actual data stored in the database at a specific point in time. It includes the current values of records and entities stored in the database.
- **Examples**:
  - In a university database schema, the schema defines tables for students, courses, and grades with their respective attributes and relationships.
  - A database instance of the university database includes actual student records, course information, and grades entered and stored in the database.

## Three-schema Architecture
- **Purpose**:
  - Supports the characteristics of a DBMS by providing program-data independence and allowing multiple views of the data.
  - Aims to separate the user applications from the physical database storage to enhance flexibility, security, and data independence.
- **Components**:
  - **External Schema (View Level)**: Describes the various user views of the database. Each external schema represents a different perspective of the data tailored to specific user requirements.
  - **Conceptual Schema (Logical Level)**: Represents the overall logical structure of the entire database for a community of users. It defines entities, attributes, relationships, and constraints without specifying physical storage details.
  - **Internal Schema (Physical Level)**: Describes the physical storage structures and access paths used to store and retrieve data efficiently. It includes details such as indexes, data storage formats, and access methods.
- **Benefits**:
  - **Program-Data Independence**: Changes in the physical storage structure do not affect the application programs, ensuring flexibility and adaptability.
  - **Multiple Views**: Different users can have customized views of the database without impacting the underlying data model or storage.
- **Example**:
  - **Scenario**: Consider a university database system that stores information about students, courses, and grades.
  - **External Schema**:
    - Student View: Shows student details such as name, ID, and courses enrolled.
    - Professor View: Displays professor information along with courses taught and department details.
  - **Conceptual Schema**:
    - Defines entities like Student, Course, and Professor with their attributes and relationships.
    - Specifies constraints such as unique student IDs and course prerequisites.
  - **Internal Schema**:
    - Includes physical storage details like data file organization, indexing structures, and access paths.
    - Specifies how data is stored on disk, such as using B-trees for indexing student records.
  - **Usage**:
    - A student accessing the database interacts with the external schema to view personal information and course schedules.
    - An administrator modifies the database structure at the conceptual schema level to add new courses or update student records without affecting user applications.
    - The DBMS translates user queries from the external schema to the internal schema for efficient data retrieval and storage operations.

## Database Languages and Interfaces
- **Database Languages**:
  - **Data Definition Language (DDL)**:
    - Used to define the database structure and schema, including creating, modifying, and deleting database objects such as tables, indexes, and views.
    - Examples of DDL commands include `CREATE`, `ALTER`, and `DROP` for defining and modifying database objects.
  - **Data Manipulation Language (DML)**:
    - Used to retrieve, insert, update, and delete data in the database.
    - DML commands allow users to perform operations on the data stored in the database tables.
    - Examples of DML commands include `SELECT`, `INSERT`, `UPDATE`, and `DELETE` for querying and manipulating data.
  - **High-Level or Non-procedural Languages**:
    - Includes languages like SQL (Structured Query Language) that provide a declarative approach to interact with databases.
    - Users specify what data they want to retrieve or manipulate without specifying how to achieve it.
    - SQL is widely used for database operations due to its simplicity and effectiveness in querying and managing relational databases.
  - **Low-Level or Procedural Languages**:
    - Require users to specify detailed steps or procedures to perform database operations.
    - These languages are typically embedded within programming languages to interact with the database at a lower level.
    - Examples include PL/SQL (Procedural Language/SQL) for Oracle databases and T-SQL (Transact-SQL) for Microsoft SQL Server.
- **Database Interfaces**:
  - **Query Languages**:
    - Provide a way for users to interact with the database by writing queries to retrieve specific data or perform operations.
    - Interfaces like command-line tools, graphical user interfaces (GUIs), and web-based interfaces allow users to input queries and view results.
  - **Application Programming Interfaces (APIs)**:
    - Enable developers to integrate database functionality into applications by providing a set of functions or methods to interact with the database.
    - APIs abstract the complexity of database operations, allowing developers to focus on application logic rather than database interactions.
  - **Object-Relational Mapping (ORM)**:
    - Bridges the gap between object-oriented programming languages and relational databases by mapping objects to database tables.
    - ORM frameworks like Hibernate (for Java) and Entity Framework (for .NET) simplify database interactions by handling object-relational mapping automatically.
  - **Middleware**:
    - Acts as a mediator between applications and databases, providing a layer of abstraction for communication.
    - Middleware components facilitate data exchange, transaction management, and security between applications and databases.
