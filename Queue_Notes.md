# Table of Contents

| Sl No. | Topic                                                                   |
| ------ | ----------------------------------------------------------------------- |
| 1.     | [Queue](#queue)                                                         |
| 2.     | [Priority Queue](#priority-queue)                                       |
| 3.     | [Monotonic Queue](#monotonic-queue)                                       |
| 4.     | [Some intresting problems on Queue](#some-intresting-problems-on-queue) |

---

# Subtopics

| Sl No. | Topic                                                                                         |
| ------ | --------------------------------------------------------------------------------------------- |
| 1.1    | [Types of Queue](#1-types-of-queue)                                                           |
| 1.2    | [Operations on Queue](#2-operations-on-queue)                                                 |
| 1.3    | [Applications of Queue](#3-applications-of-queue)                                             |
| 1.4    | [Time complexity of Queue Operations](#time-complexity-of-queue-operations)                   |
| 2.1    | [Adding custom comparator](#1-adding-custom-comparator)                                       |
| 2.2    | [Operations on Priority Queue](#2-operations-on-priority-queue)                               |
| 2.3    | [Time complexity of Priority Queue Operations](#time-complexity-of-priority-queue-operations) |

---

# Queue

Queue is a linear data structure that follows the First In First Out (FIFO) principle. The elements are inserted at the rear end and deleted from the front end. The element that is inserted first is the one that is deleted first.

## 1. Types of Queue

There are multiple types of Queues.

- Simple Queue
- Circular Queue
- Priority Queue
- Dequeue ( Double Ended Queue )

Double Ended Queue is a queue in which the elements can be inserted and deleted from both the ends. Hence it might not follow the FIFO principle.

In circular queue, the rear end is connected to the front end. This basically means that once rear reaches the end of the queue, it wraps around to the front of the queue.

Priority Queue is a queue in which the elements are inserted based on their priority. The element with the highest priority is available at the front end of the queue.

> In c++ higher the number, higher the priority.
> In Java, lower the number, higher the priority.

## 2. Operations on Queue

We will be using the inbuilt STL implementation of Queue in C++.

```cpp
#include <queue>
using namespace std;
queue<int> q;
```

We can also use an array to implement a queue.

```cpp
int q[100], front = -1, rear = -1;
void enqueue(int x) {
    if (front == -1) front = 0;
    q[++rear] = x;
}
void dequeue() {
    if (front == rear) front = rear = -1;
    else front++;
}
int front() {
    return q[front];
}
```

### 2.1 Enqueue

An element will be appended to the rear end of the queue.

```cpp
q.push(10);
q.push(20);
q.push(30);
```

```
Queue: 10 20 30
```

### 2.2 Dequeue

Element will be removed from the front end of the queue.

```cpp
q.pop(); // Removes 10
```

```
Queue: 20 30
```

### 2.3 Front

Access the element at the front end of the queue.

```cpp
cout << q.front(); // 20
```

### 2.4 Back

Access the element at the rear end of the queue.

```cpp
cout << q.back(); // 30
```

### 2.5 Size

Gives the number of elements in the queue.

```cpp
cout << q.size(); // 2
```

### 2.6 Empty

Returns true if the queue is empty, else returns false;

```cpp
cout << q.empty(); // 0
```

### Time complexity of Queue Operations

| Operation | Time Complexity |
| --------- | --------------- |
| Enqueue   | O(1)            |
| Dequeue   | O(1)            |
| Front     | O(1)            |
| Back      | O(1)            |
| Size      | O(1)            |
| Empty     | O(1)            |

## 3. Applications of Queue

Queues are widely used in various applications like data processing, CPU scheduling, Disk Scheduling, etc.

Some common applications of Queue are:

- **Task Scheduling**: In Operating Systems, tasks are scheduled based on the priority of the task. Priority maybe the time of arrival or the time required to complete the task.
- **Breadth First Search**: In Graphs, BFS uses a queue to store the nodes that are to be visited.
- **Resource Allocation**: Queues are used to manage and allocate resources such as I/O devices, CPU, etc.
- **Message Buffers**: Queues are used to store messages in the message buffer.
- **Network Packet Handling**: Queues are used to store packets in the network buffer. This helps to make sure that the packets are sent in the order they are received.

### 3.1 Applications of Queue in Operating systems:

- Semaphores
- FCFS ( first come first serve) scheduling, example: FIFO queue
- Spooling in printers
- Buffer for devices like keyboard
- CPU Scheduling
- Memory management

---

# Priority Queue

These are the queues in which the elements are inserted based on their priority. The element with the highest priority is available at the front end of the queue.

In C++ STL the priority queue is implemented using the priority_queue class.
It uses a max heap to store the elements.
Hence elements are stored in descending order of their priority.

```cpp
#include <queue>
using namespace std;
priority_queue<int> pq;
```

This will create a default priority queue in C++.

## 1. Adding custom comparator

Custom comparator helps to convert the default max heap to min heap.
It also helps us to decide priority based on the different data structures which is being stored on the priority queue.

```cpp
priority_queue<int, vector<int>, greater<int>> pq;
```

This will create a min heap priority queue.

Similarly lets say we want to store a pair of integers in the priority queue and we want to sort them based on the first element of the pair.

```cpp
priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> pq;
// Here an underlying container also is declared.
```

Lets say we want to sort the pair based on the second element of the pair.

```cpp
class Compare {
public:
    bool operator() (pair<int, int> a, pair<int, int> b) {
        return a.second > b.second;
    }
};
priority_queue<pair<int, int>, vector<pair<int, int>>, Compare> pq;
```

Priority queues are versatile and can be used in a variety of applications.

## 2. Operations on Priority Queue

Priority Queue supports the operations similar to the queue.

### 2.1 Insert

An element will be inserted into the priority queue.

```cpp
pq.push(10);
pq.push(20);
pq.push(30);
```

```
Queue: 30 20 10
```

### 2.2 Pop

Deletes the element with the highest priority.

```cpp
pq.pop(); // Removes 30
```

```
Queue: 20 10
```

### 2.3 Top

Returns the element with the highest priority.

```cpp
cout << pq.top(); // 20
```

### 2.4 Size

Returns the number of elements in the priority queue.

```cpp
cout << pq.size(); // 2
```

### 2.5 Empty

Returns true if the priority queue is empty, else returns false.

```cpp
cout << pq.empty(); // 0
```

### Time complexity of Priority Queue Operations

Since priority queue is implemented using heap, the time complexity of the operations are as follows:
| Operation | Time Complexity |
| --------- | --------------- |
| Insert | O(log n) |
| Pop | O(log n) |
| Top | O(1) |
| Size | O(1) |
| Empty | O(1) |

If we queue n elements into the priority queue, the time complexity will be O(n log n).

---

# Monotonic Queue

A queue which allows for a way to find the smallest/largest element of the queue in `O(1)`, is called a monotonic queue.

It has a big disadvantage though, because the modified queue will actually not store all elements.

## Idea

The key idea is to store the items in the queue that are needed to determine the minimum. Namely we will keep the queue in nondecreasing order(i.e. the smallest value will be stored in the head), the actual minimum has to be always contained in the queue. This way the samllest element will always be in the head of the queue. 

Before adding a new element to the queue, it is enough to make a "cut": we will remove all trailing  elements of the queue that are larger than the new element, and afterwards add the new element to the queue. This way we don't break the order of the queue, and we will also not loose the current element if it is at any subsequent step, the minmum. All the elements that we removed can never be a minimum itself, so this operation is allowed. When we want to extract an element from the head, it actually might not be there (because we removed it previously while adding a smaller element). Therefore when deleting an element from a queue we need to know the value of the element. If the head of the queue has the same value, we can safely remove it, otherwise we do nothing. 

## Implementation

Consider the implementations of the above operations: 

### Init
```cp
deque<int> q;
```

### Finding minimum
```cp
int minimum = q.front();
```
### Adding an element
```cp
while(!q.empty() && q.back() > new_element)
    q.pop_back();
q.push_back(new_element);
```
### Removing an element
```cp
if(!q.empty() && q.front() == remove_element)
    q.pop_front();
```
## Examples Problems

The above implementation is very specific and might need to be modified depending on the nature of the problem


+ ![Queries with Fixed Length](https://www.hackerrank.com/challenges/queries-with-fixed-length/problem)
+ ![Binary Land](https://www.codechef.com/MAY20A/problems/BINLAND)
# Some intresting problems on Queue

## 1. Implement Queue using Stack

We need two stacks to implement a queue using stacks. One stack is used for enqueue operation and the other stack is used for dequeue operation.
The operations needed to be implemented are:

1. Enqueue
2. Dequeue
3. Front
4. Empty

```cpp
class MyQueue {
    public:
    stack<int> s1, s2;
    void enqueue(int x) {
        s1.push(x);
    }
    void dequeue() {
        if (s2.empty()) {
            while (!s1.empty()) {
                s2.push(s1.top());
                s1.pop();
            }
        }
        s2.pop();
    }
    int front() {
        if (s2.empty()) {
            while (!s1.empty()) {
                s2.push(s1.top());
                s1.pop();
            }
        }
        return s2.top();
    }
    bool empty() {
        return s1.empty() && s2.empty();
    }
};
```

## 2. Implement Stack using Queue

We need two queues to implement a stack using queues. One queue is used for push operation and the other queue is used for pop operation.
The operations needed to be implemented are:

- Push
- Pop
- Top
- Empty

```cpp
class MyStack {
    public:
    queue<int> q1, q2;
    void push(int x) {
        while(!q1.empty()) {
            q2.push(q1.front());
            q1.pop();
        }
        q1.push(x);
        while(!q2.empty()) {
            q1.push(q2.front());
            q2.pop();
        }
    }
    void pop() {
        q1.pop();
    }
    int top() {
        return q1.front();
    }
    bool empty() {
        return q1.empty();
    }
};
```
