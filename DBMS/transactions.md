# Transactions in Database Systems

## Table of Contents
1. [Transaction Concept](#transaction-concept)
2. [Example of Fund Transfer](#example-of-fund-transfer)
3. [ACID Properties](#acid-properties)
4. [Transaction State](#transaction-state)
5. [Concurrent Executions](#concurrent-executions)
6. [Schedules](#schedules)
7. [Serializability](#serializability)
8. [Conflict Serializability](#conflict-serializability)
9. [View Serializability](#view-serializability)
10. [Testing for Serializability](#testing-for-serializability)
11. [Recoverable Schedules](#recoverable-schedules)
12. [Cascading Rollbacks](#cascading-rollbacks)
13. [Cascadeless Schedules](#cascadeless-schedules)
14. [Concurrency Control](#concurrency-control)
15. [Concurrency Control vs. Serializability Tests](#concurrency-control-vs-serializability-tests)
16. [Weak Levels of Consistency](#weak-levels-of-consistency)
17. [Levels of Consistency in SQL-92](#levels-of-consistency-in-sql-92)

## Transaction Concept

A transaction is a unit of program execution that accesses and possibly updates various data items.

### Example:
- Transaction to transfer $50 from account A to account B:
  1. `read(A)`
  2. `A := A – 50`
  3. `write(A)`
  4. `read(B)`
  5. `B := B + 50`
  6. `write(B)`

### Issues:
1. **Failures:** Hardware or software failures that may interrupt the transaction.
2. **Concurrency:** Multiple transactions executing concurrently may lead to inconsistencies.

## Example of Fund Transfer

### Steps:
1. `read(A)`
2. `A := A – 50`
3. `write(A)`
4. `read(B)`
5. `B := B + 50`
6. `write(B)`

### Requirements:
- **Atomicity:** Ensures incomplete transactions don't leave partial updates.
- **Durability:** Completed transactions persist despite failures.
- **Consistency:** Ensures the database remains consistent before and after transactions.
- **Isolation:** Ensures concurrent transactions do not interfere with each other.

## ACID Properties

- **Atomicity:** All or none of the transaction's operations are reflected.
- **Consistency:** Each transaction preserves database consistency.
- **Isolation:** Each transaction operates independently of others.
- **Durability:** Changes from a committed transaction persist even after a failure.

## Transaction State

- **Active:** Initial state while executing.
- **Partially Committed:** After the final statement is executed.
- **Failed:** If normal execution cannot proceed.
- **Aborted:** After rollback and restoration to the initial state.
- **Committed:** After successful completion.

## Concurrent Executions

Multiple transactions run concurrently, offering:
- **Increased Utilization:** Better CPU and disk usage.
- **Reduced Response Time:** Short transactions don't wait for long ones.

## Schedules

A sequence of instructions defining the order of execution for concurrent transactions.

### Examples:
- **Schedule 1:** T1 followed by T2.
- **Schedule 2:** T2 followed by T1.
- **Schedule 3:** Non-serial but equivalent to Schedule 1.

## Serializability

A schedule is serializable if it is equivalent to a serial schedule.

### Types:
1. **Conflict Serializability:** Based on the order of conflicting operations.
2. **View Serializability:** Based on the values read and written.

## Conflict Serializability

If a schedule can be transformed into a serial schedule by swapping non-conflicting operations, it is conflict serializable.

## View Serializability

Schedules are view equivalent if:
1. Initial reads are identical.
2. Read operations read the same values.
3. Final writes are identical.

## Testing for Serializability

- **Precedence Graph:** A graph with transactions as nodes and edges representing conflicts.
- **Acyclic Graph:** Indicates conflict serializable schedules.

## Recoverable Schedules

A schedule is recoverable if transactions commit only after all transactions they depend on commit.

## Cascading Rollbacks

A failure in one transaction may cause others to roll back, undoing significant work.

## Cascadeless Schedules

Schedules ensuring no cascading rollbacks by committing transactions before dependent transactions read their data.

## Concurrency Control

Mechanisms to ensure schedules are:
- **Serializable:** Conflict or view serializable.
- **Recoverable and Cascadeless**

## Concurrency Control vs. Serializability Tests

Concurrency control protocols ensure serializability without directly testing the precedence graph.

## Weak Levels of Consistency

Applications may accept weaker consistency for performance gains, such as approximate data for read-only transactions.

## Levels of Consistency in SQL-92

- **Serializable:** Default level.
- **Repeatable Read:** Ensures repeated reads return the same data, but may not be serializable.
