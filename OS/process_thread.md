# Process and Process Scheduling

## Table of Contents
1. [Introduction to Processes](#introduction-to-processes)
2. [Process Control Block (PCB)](#process-control-block-pcb)
3. [Process Scheduling](#process-scheduling)
    1. [Schedulers](#schedulers)
    2. [Context Switching](#context-switching)
4. [Process Creation and Termination](#process-creation-and-termination)
5. [Interprocess Communication](#interprocess-communication)
6. [Threads and Multithreading](#threads-and-multithreading)
7. [CPU Scheduling](#cpu-scheduling)
    1. [Scheduling Criteria](#scheduling-criteria)
    2. [Scheduling Algorithms](#scheduling-algorithms)
8. [Comparison of Scheduling Algorithms](#comparison-of-scheduling-algorithms)
9. [Multiple Processor Scheduling](#multiple-processor-scheduling)

## Introduction to Processes
A process is a program in execution and a unit of work in a computer system. The terms process and job are used interchangeably. A process consists of:
- Text section containing the program code
- Current activity represented by the values of the program counter and other registers
- Program stack
- Data section containing global variables
- Heap

A program is a passive entity while a process is an active entity. Process state is defined by the current activity of the process, which changes as the process executes. Only one process can be in the running state at any instant, but many processes can be ready or waiting.

## Process Control Block (PCB)
Each process is represented internally by the operating system with a process control block (PCB), also called a task control block. The PCB contains all information associated with the process:
- Process state
- Values of program counter and other registers
- CPU scheduling information (priority, pointer to scheduling queue, etc.)
- Accounting information (process ID, CPU and real-time used, time limits, etc.)
- I/O status information (list of I/O devices allocated, list of open files, etc.)

## Process Scheduling
Process scheduling involves selecting one process for execution out of all the ready processes. The objective of multiprogramming is to have some process running at all times to maximize CPU utilization, while multitasking aims to switch the CPU among processes frequently enough for user interaction with each process.

### Schedulers
There are three types of schedulers:
- **Long-term scheduler (job scheduler):** Selects processes from those submitted by the user and loads them into memory, controlling the degree of multiprogramming.
- **Short-term scheduler (CPU scheduler):** Selects one of the processes in memory and allocates the CPU to it, invoked frequently.
- **Medium-term scheduler:** Removes processes from memory to reduce multiprogramming, later reintroducing them (swapping).

### Context Switching
Context switching involves saving the state of the current process and reloading the state of another process. States are saved into and reloaded from PCBs. Context-switch time is a pure overhead, highly dependent on hardware.

## Process Creation and Termination
Process creation involves one process creating another, called the parent and child processes, respectively. Processes are identified by unique IDs and may obtain resources from their parent or directly from the operating system. Process termination marks the deletion of the PCB of the process. A parent process may terminate a child process for various reasons, such as exceeding resource usage or if the parent process is terminating.

## Interprocess Communication
Reasons for interprocess communication include information sharing, computational speedup, modularity, and convenience. Communication models include:
- Shared memory
- Message passing (send(P, message) and receive(id, message))

## Threads and Multithreading
A thread is the smallest sequence of instructions that can be managed independently by a scheduler, existing as part of a process. Multiple threads within a process share resources like memory. Differences between processes and threads include:
- Processes are typically independent, while threads exist as parts of a process.
- Processes carry more state information, whereas threads share process state and resources.
- Processes have separate address spaces, while threads share an address space.
- Context switching between threads is faster than between processes.

Advantages of multithreading include responsiveness, faster execution, better resource utilization, easy communication, and parallelization.

## CPU Scheduling
The execution of a process consists of alternate CPU bursts and I/O bursts, starting and ending with CPU bursts. The CPU scheduler is invoked when a process:
1. Switches from running to waiting state
2. Switches from running to ready state
3. Switches from waiting to ready state
4. Terminates

In non-preemptive scheduling, a process keeps the CPU until it terminates or switches to the waiting state. In preemptive scheduling, a process can be forced to leave the CPU and switch to the ready queue.

### Scheduling Criteria
- **CPU utilization:** Increase the percentage of time the CPU is busy.
- **Throughput:** Increase the number of processes completed per unit time.
- **Turnaround time:** Decrease the time from submission to completion.
- **Waiting time:** Decrease the time a process spends in the ready queue.
- **Response time:** Decrease the time from submission to first response.

### Scheduling Algorithms
Several well-known scheduling algorithms include:
- **First-Come First-Served (FCFS):** Non-preemptive, high average waiting time.
- **Shortest Job First (SJF):** Selects the process with the smallest next CPU burst, can be preemptive or non-preemptive.
- **Priority Scheduling:** Allocates CPU to the process with the highest priority, can be preemptive or non-preemptive.
- **Round Robin (RR):** Uses a small time quantum, preemptive.
- **Multilevel Queue Scheduling:** Partitions the ready queue into several queues, each with its own scheduling algorithm.
- **Multilevel Feedback Queue Scheduling:** Allows processes to move between queues, preemptive priority scheduling.

## Comparison of Scheduling Algorithms
- **First-Come First-Served:** Simple but inefficient.
- **Shortest Job First:** Most efficient but hard to implement.
- **Priority Scheduling:** Low waiting time for high priority processes, may cause starvation.
- **Round Robin:** Efficient with no indefinite blocking but may have high context switching.
- **Multilevel Queue:** Low waiting time for high priority processes, complex.
- **Multilevel Feedback Queue:** Fast turnaround for short processes, complex.

## Multiple Processor Scheduling
In multiprocessor systems, CPUs can be scheduled asymmetrically or symmetrically:
- **Asymmetric multiprocessing:** One processor schedules for all.
- **Symmetric multiprocessing:** Each processor self-schedules.

Processor affinity attempts to keep a process on a given processor to avoid the high cost of migrating processes. Load balancing ensures all processors are equally loaded, applicable only in symmetric systems.

Chapters: 3 – 5.
Sections: 3.1 – 3.4, 4.1, 4.2, and 5.1
