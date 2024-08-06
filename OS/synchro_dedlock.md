# Table of Contents
1. [Process Synchronization](#process-synchronization)
   1. [Introduction](#introduction)
   2. [Race Condition](#race-condition)
   3. [Critical Section Problem](#critical-section-problem)
   4. [Peterson's Solution](#petersons-solution)
   5. [Semaphores](#semaphores)
   6. [Producers-Consumers Problem](#producers-consumers-problem)
   7. [Readers-Writers Problem](#readers-writers-problem)
   8. [Dining Philosophers Problem](#dining-philosophers-problem)
   9. [Monitors](#monitors)
2. [Deadlocks](#deadlocks)
   1. [Introduction](#introduction-1)
   2. [Necessary Conditions](#necessary-conditions)
   3. [Resource Allocation Graph](#resource-allocation-graph)
   4. [Methods for Handling Deadlocks](#methods-for-handling-deadlocks)
   5. [Banker's Algorithm](#bankers-algorithm)
   6. [Deadlock Detection](#deadlock-detection)
   7. [Recovery from Deadlock](#recovery-from-deadlock)

# Process Synchronization

## Introduction
A cooperating process is one that can affect or be affected by other processes executing in the system.

## Race Condition
Race condition is a situation where several processes access and manipulate the same data concurrently, and the outcome depends on the particular order in which the accesses take place. To avoid such situations, it must be ensured that only one process can manipulate the data at a given time through process synchronization.

## Critical Section Problem
A critical section problem involves ensuring that when one process is executing in its critical section, no other process can execute its critical section. It is defined as follows:
- There are n processes, viz. P0, P1, P2 ... Pn-1.
- Each process has a section of code, called the critical section, in which the process changes common variables and files.
- The problem is to ensure mutual exclusion, progress, and bounded waiting.

## Peterson's Solution
Peterson’s solution works for two processes using shared variables:
```c
int turn;
Boolean flag[2];
do {
    flag[i] = true;
    turn = j;
    while (flag[j] && turn == j);
    // critical section
    flag[i] = FALSE;
    // remainder section
} while (true);
```
This solution satisfies mutual exclusion, progress, and bounded waiting properties.

## Semaphores
A semaphore is an integer variable that is accessed only through two atomic operations called wait() and signal().

```c
wait(S) {
    while (S <= 0);
    S--;
}

signal(S) {
    S++;
}
```
Semaphores can be binary (mutex) or counting, and they are used to solve the critical section problem with multiple processes.

## Producers-Consumers Problem
In the bounded buffer problem:

Semaphores: mutex = 1; empty = n; full = 0;
Producers and consumers use these semaphores to synchronize access to the buffer.

## Readers-Writers Problem
Shared data:

int readcount = 0;
Semaphores: mutex = 1; wrt = 1;
Writers and readers use these semaphores to ensure mutual exclusion and synchronization.

## Dining Philosophers Problem
Philosophers use semaphores to pick up and put down chopsticks.

```c
do {
    wait(chopstick[i]);
    wait(chopstick[(i+1)%5]);
    // eat
    signal(chopstick[i]);
    signal(chopstick[(i+1)%5]);
    // think
} while (true);
```
This problem illustrates the challenges of avoiding deadlock in process synchronization.

## Monitors
A monitor is a high-level synchronization construct that provides mutual exclusion and allows condition variables to be used for synchronization.

```c
monitor monitor_name {
    // shared variable declarations
    initialization_code (...) { ... }
    procedure P1 (...) { ... }
    procedure Pn (...) { ... }
}
```

# Deadlocks
## Introduction
In a multiprogramming system, several processes may compete for a finite number of resources. Deadlock is a situation where two or more processes are waiting indefinitely because the resources they have requested are being held by one another.

## Necessary Conditions
Deadlocks can occur if the following conditions hold simultaneously:

Mutual exclusion
Hold and wait
No preemption
Circular wait
Resource Allocation Graph
A cycle in the resource allocation graph implies that there may be a deadlock. If each resource type has one instance, a cycle implies a deadlock.

## Methods for Handling Deadlocks
Deadlock Prevention: Ensure that at least one of the necessary conditions for deadlock cannot hold.
Deadlock Avoidance: Use algorithms like the Banker’s algorithm to avoid deadlock.
Deadlock Detection and Recovery: Detect deadlocks and recover from them through process termination or resource preemption.

## Banker's Algorithm
The Banker’s algorithm is used to avoid deadlock by ensuring that the system remains in a safe state.

Data structures: Available[m], Max[nxm], Allocation[nxm], Need[nxm].
Safety algorithm: Checks if the system is in a safe state.
Resource-request algorithm: Checks if a request can be safely granted.

## Deadlock Detection
If all resource types have single instances, deadlocks can be detected using a wait-for graph. A cycle in the wait-for graph denotes deadlock.

## Recovery from Deadlock
Process Termination: Abort all deadlocked processes or abort one process at a time until the deadlock is broken.
Resource Preemption: Select a victim, rollback, and handle starvation.