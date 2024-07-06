# Relational Algebra in SQL

## Table of Contents

1. [Introduction](#introduction)
2. [Basic Operations](#basic-operations)
   - [Select (σ)](#select-σ)
   - [Project (π)](#project-π)
   - [Rename (ρ)](#rename-ρ)
3. [Joins](#joins)
   - [Inner Join](#inner-join)
   - [Outer Join](#outer-join)
     - [Left Outer Join](#left-outer-join)
     - [Right Outer Join](#right-outer-join)
     - [Full Outer Join](#full-outer-join)
4. [Set Operations](#set-operations)
   - [Union (∪)](#union-∪)
   - [Intersection (∩)](#intersection-∩)
   - [Difference (−)](#difference-−)
   - [Cartesian Product (×)](#cartesian-product-×)
5. [Aggregate Functions](#aggregate-functions)
   - [Count](#count)
   - [Sum](#sum)
   - [Average](#average)
   - [Min](#min)
   - [Max](#max)
6. [Main Points to Remember](#main-points-to-remember)

## Introduction

Relational algebra is a procedural query language that works on relational model. It consists of a set of operations that take one or two relations as input and produce a new relation as output.

## Basic Operations

### Select (σ)

The Select operation selects tuples that satisfy a given predicate.

**Syntax:**
σ_age > 18_(students)

This selects all students where age is greater than 18.

### Project (π)
The Project operation selects certain columns from the relation.

**Syntax:**
π_column1, column2, ... (relation)

**Example:**
π_name, age_(students)

This projects the name and age columns from the students relation.

### Rename (ρ)
The Rename operation renames the output relation or its attributes.

**Syntax:**
ρ_newRelationName(oldRelation)

**Example:**
ρ_studentsRenamed(students)

## Joins

### Inner Join
An Inner Join returns tuples that have matching values in both relations.

**Syntax:**
relation1 ⨝_condition_relation2

**Example:**
students ⨝_students.id = enrollments.student_id_enrollments


### Outer Join

#### Left Outer Join
Returns all tuples from the left relation and the matched tuples from the right relation. If no match is found, NULL values are filled in for columns from the right relation.

**Syntax:**
relation1 ⟕_condition_relation2


#### Right Outer Join
Returns all tuples from the right relation and the matched tuples from the left relation. If no match is found, NULL values are filled in for columns from the left relation.

**Syntax:**
relation1 ⟖_condition_relation2


#### Full Outer Join
Returns all tuples when there is a match in either left or right relation. If there is no match, the result is NULL on the side that does not have a match.

**Syntax:**
relation1 ⟗_condition_relation2


## Set Operations

### Union (∪)
The Union operation combines tuples from two relations, removing duplicates.

**Syntax:**
relation1 ∪ relation2



### Intersection (∩)
The Intersection operation returns tuples that are present in both relations.

**Syntax:**
relation1 ∩ relation2


### Difference (−)
The Difference operation returns tuples that are in the first relation but not in the second.

**Syntax:**
relation1 − relation2


### Cartesian Product (×)
The Cartesian Product returns a relation that is the concatenation of every tuple of the first relation with every tuple of the second relation.

**Syntax:**
relation1 × relation2


**Example:**
students × courses



## Aggregate Functions
Aggregate functions perform a calculation on a set of values and return a single value.

### Count
Counts the number of tuples.

**Syntax:**
COUNT(relation)


### Sum
Calculates the sum of attribute values.

**Syntax:**
SUM(attribute)(relation)


### Average
Calculates the average of attribute values.

**Syntax:**
AVG(attribute)(relation)


### Min
Finds the minimum attribute value.

**Syntax:**
MIN(attribute)(relation)


### Max
Finds the maximum attribute value.

**Syntax:**
MAX(attribute)(relation)

## Main Points to Remember
- **Select (σ)** is used for filtering rows.
- **Project (π)** is used for selecting columns.
- **Rename (ρ)** is used to rename relations and attributes.
- **Joins** are used to combine relations based on a condition.
    - Inner Join returns matching tuples.
    - Outer Joins (Left, Right, Full) return matching tuples and include non-matching tuples with NULLs.
- **Set Operations** combine results from two relations.
    - Union combines all tuples.
    - Intersection returns common tuples.
    - Difference returns tuples from the first relation not present in the second.
    - Cartesian Product returns all possible pairs of tuples.
- **Aggregate Functions** perform calculations on sets of values.
