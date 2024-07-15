# NoSQL Overview
## Introduction to NoSQL
- NoSQL databases are a hot topic in computing with over a hundred different products.
- Differ from traditional RDBMS in storage and manipulation of data.
- Ideal for large datasets, distributed systems, and applications requiring high scalability and performance.

## Key Concepts of NoSQL
### Data Storage and Manipulation
- **Data stored in columns and tables**
- **Relationships represented by data**
- **Data Manipulation Language (DML)**
- **Data Definition Language (DDL)**
- **Transactions**
- **Abstraction from physical layer**: Applications specify what, not how.
- **In Memory Databases**

### ACID Properties
- **Atomicity**: All operations in a transaction complete or none do.
- **Consistency**: Transactions transform the database from one consistent state to another.
- **Isolation**: Results of changes are not visible until the transaction commits.
- **Durability**: Results of committed transactions survive failures.

## NoSQL Characteristics
- **No Relational / No RDBMS / Not Only SQL**
- A class of products and a collection of concepts for data storage and manipulation.
- Non-relational DBMSs are not new but have gained popularity due to scalable internet applications.
- **Key NoSQL Papers**:
  - BigTable (Google)
  - Dynamo (Amazon)

## NoSQL and Big Data
- **Big Data**: Often related to NoSQL due to its large volume and need for efficient storage and access.
- Challenges:
  - Efficiently storing and accessing large amounts of data.
  - Managing evolving schemas and metadata.
  - Handling massive, sparse datasets.

## Types of NoSQL Databases
### Sorted Ordered Column Store
- Optimized for queries over large datasets.
- Stores columns of data together.

### Document Databases
- Pair each key with a complex data structure known as a document (e.g., XML, JSON).
- Notable Examples: MongoDB, CouchDB.

### Key-Value Stores
- Simplest form of NoSQL databases.
- Each item is stored as an attribute name (key) with its value.
- Notable Examples: Couchbase, Redis, Amazon Dynamo.

### Graph Databases
- Used to store information about networks of data, such as social connections.
- Notable Examples: Neo4j.

## NoSQL Scalability
- **Vertical Scaling**: Upgrading the server with faster CPUs or more memory.
- **Horizontal Scaling**: Adding more machines to the cluster.
- Approaches include Master-slave, Sharding (partitioning).

## ACID vs. BASE Properties
- **ACID**: Atomicity, Consistency, Isolation, Durability.
- **BASE**: Basically Available, Soft state, Eventually consistent.
- CAP Theorem: Consistency, Availability, Partition Tolerance.

## NoSQL Use Cases
- Large, uncontrolled, unstructured data.
- Examples: Log analysis, social networking feeds, external data feeds, time-based data.

## Examples of NoSQL Operations
### Cassandra
- Creating and managing keyspaces and tables:
  ```sql
  CREATE KEYSPACE mykeyspace;
  USE mykeyspace;
  CREATE TABLE student (name text, usn text, mob int, id int, PRIMARY KEY(id));
  ```
  
### MongoDB
Basic operations:

use mydatabase;
db.createCollection('mycollection');
db.mycollection.insert({name: 'John', age: 30});
db.mycollection.find();

### Redis
Basic commands:

SET name "John";
GET name;
DEL name;
EXISTS name;

## Programming Patterns for NoSQL
Create a connection (session).
Execute queries using the session.
Close the session.
### Python Example (MongoDB)

import pymongo
from pymongo import MongoClient

cluster = MongoClient("mongodb://<username>:<password>@<host>:<port>")
db = cluster["mydatabase"]
collection = db["mycollection"]
post = {"name": "John", "email": "john@example.com"}
collection.insert_one(post)

## Conclusion
NoSQL databases offer various advantages for specific use cases, particularly involving large volumes of semi-structured or unstructured data.
They provide scalability, flexibility, and performance benefits over traditional RDBMS in many scenarios.
Selecting the right NoSQL solution depends on the specific requirements and goals of the application.