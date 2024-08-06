# MEMORY MANAGEMENT

## Table of Contents
1. [Multistep Processing of a User Program](#multistep-processing-of-a-user-program)
2. [Memory Management Unit (Hardware)](#memory-management-unit-hardware)
3. [Swapping](#swapping)
   - [Swap-Out, Swap-In](#swap-out-swap-in)
   - [Priority Scheduling: Roll-Out, Roll-In](#priority-scheduling-roll-out-roll-in)
   - [Relocation](#relocation)
4. [Contiguous Memory Allocation](#contiguous-memory-allocation)
   - [Static Allocation](#static-allocation)
   - [Dynamic Allocation](#dynamic-allocation)
   - [External Fragmentation](#external-fragmentation)
5. [Paging](#paging)
   - [Advantages and Disadvantages](#advantages-and-disadvantages)
   - [Page Table and Transition Look-Aside Buffer (TLB)](#page-table-and-transition-look-aside-buffer-tlb)
   - [Shared Pages and Reentrant Code](#shared-pages-and-reentrant-code)
6. [Hierarchical Page Tables](#hierarchical-page-tables)
7. [Hashed Page Table](#hashed-page-table)
8. [Inverted Page Table](#inverted-page-table)
9. [Segmentation](#segmentation)

## Multistep Processing of a User Program
Detailed steps involved in processing a user program, including the role of the source program, compiler, linker, and loader in transforming it into a process in memory.

## Memory Management Unit (Hardware)
Description of the hardware component responsible for managing memory access and translation between logical and physical addresses.

## Swapping
### Swap-Out, Swap-In
Explanation of the swapping process, where processes are moved in and out of memory.
### Priority Scheduling: Roll-Out, Roll-In
Details on how priority scheduling affects swapping, with processes being rolled out and rolled in based on priority.
### Relocation
The importance of relocation in memory management and how it facilitates swapping.

## Contiguous Memory Allocation
### Static Allocation
- Dividing memory into fixed-sized blocks.
- Allocating one block to each process.
- Control of multiprogramming by the number of partitions.

### Dynamic Allocation
- Allocating available space to processes as needed.
- Keeping track of holes and using strategies like first-fit, best-fit, and worst-fit.
- The issue of external fragmentation and potential solution via compaction.

### External Fragmentation
- Challenges with contiguous allocation leading to scattered memory.
- The costly solution of compaction to address fragmentation.

## Paging
Paging as a non-contiguous memory allocation scheme with equal page and frame sizes.
### Advantages and Disadvantages
- Advantages: Size independence and no external fragmentation.
- Disadvantages: Internal fragmentation.
### Page Table and Transition Look-Aside Buffer (TLB)
- Structure and function of page tables.
- Use of TLB for fast memory access.
- Calculation of effective access time.

### Shared Pages and Reentrant Code
- Concept of reentrant code.
- Sharing pages among multiple processes when containing reentrant code.

## Hierarchical Page Tables
- Structure and function of two-level and three-level paging systems.
- Address translation in hierarchical paging.

## Hashed Page Table
- Use of hashed values for virtual page numbers.
- Linked list structure to handle collisions in hash tables.

## Inverted Page Table
- Centralized table structure for memory management.
- Challenges with implementing shared pages.

## Segmentation
- Logical partitioning of memory into segments with unique purposes.
- Typical segments in a program (code, data, stack, extra).
- Hardware support for segmentation.
- Combination of segmentation and paging in processors like Intel Pentium.



# VIRTUAL MEMORY MANAGEMENT

## Table of Contents
1. [Introduction to Virtual Memory](#introduction-to-virtual-memory)
2. [Demand Paging](#demand-paging)
   - [Page Fault Handling](#page-fault-handling)
   - [Pure Demand Paging](#pure-demand-paging)
   - [Hardware Support for Virtual Memory](#hardware-support-for-virtual-memory)
3. [Page Replacement Algorithms](#page-replacement-algorithms)
   - [FIFO](#fifo)
   - [Optimal](#optimal)
   - [LRU](#lru)
   - [LRU Approximation](#lru-approximation)
4. [Allocation of Frames](#allocation-of-frames)
   - [Frame Allocation Algorithms](#frame-allocation-algorithms)
5. [Thrashing](#thrashing)
   - [Avoiding Thrashing](#avoiding-thrashing)

## Introduction to Virtual Memory
Explanation of virtual memory and its advantages in executing large programs and supporting multiprogramming.

## Demand Paging
### Page Fault Handling
Steps involved in handling a page fault, including reference, trap, locating the page on disk, loading it, and resuming execution.
### Pure Demand Paging
Starting a process execution without any pages in memory and leveraging locality of references.
### Hardware Support for Virtual Memory
Requirements for hardware support, including page table and disk.

## Page Replacement Algorithms
### FIFO
- Simple queue-based algorithm with Belady’s anomaly.
### Optimal
- Theoretical best performance with future knowledge of reference string.
### LRU
- Replacing the least-recently used page using counters or stacks.
### LRU Approximation
- Algorithms like additional-reference-bits and second chance.

## Allocation of Frames
### Frame Allocation Algorithms
- Equal allocation and proportional allocation.
- Local and global page replacement strategies.

## Thrashing
### Avoiding Thrashing
- Working-set model based on locality of references.
- Managing the degree of multiprogramming to prevent thrashing.

