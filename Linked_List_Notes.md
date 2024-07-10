# Table of Contents

| Sl. No. | Topic                       |
| ------- | --------------------------- |
| 1.      | [Linked List](#linked-list) |

---

# Subtopics

| Sl. No. | Topic                                                                                                                            |
| ------- | -------------------------------------------------------------------------------------------------------------------------------- |
| 1.1     | [Structure of a Linked List](#11-structure-of-a-linked-list)                                                                     |
| 1.2     | [Types of Linked List](#12-types-of-linked-list)                                                                                 |
| 1.3     | [Operations on Linked List](#13-operations-on-linked-list)                                                                       |
| 1.4     | [Code snippets for various operations on a Singly Linked List](#14-code-snippets-for-various-operations-on-a-singly-linked-list) |
| 1.5     | [Some tricky questions on Linked List](#15-some-tricky-questions-on-linked-list)                                                 |
| ##      |

# Linked List

A Linked list is a linear data strcuture, where elements are stored in nodes. Each node has a data field and a reference to the next node in the sequence. The last node has a reference to null.

## 1.1 Strucutre of a Linked List

- `Node` - A node is a basic unit of a linked list. It contains data and a reference to the next node.
- `Head` - The first node of a linked list is called the head.
- `Tail` - The last node of a linked list is called the tail.
- `Next` - The reference to the next node in the sequence.
- `Val` - The data stored in the node.

## 1.2 Types of Linked List

We have the following types of linked lists:

- `Singly Linked List` - Each node has a reference to the next node.
- `Doubly Linked List` - Each node has a reference to the next and the previous node.
- `Circular Linked List` - The last node has a reference to the first node.

## 1.3 Operations on Linked List

1. `Insertion` - Inserting a node in the linked list.
2. `Deletion` - Deleting a node from the linked list.
3. `Traversal` - Traversing the linked list.
4. `Searching` - Searching for a node in the linked list.

## 1.4 Code snippets for various operations on a Singly Linked List

Assume structure of Singly Linked List is as follows:

```cpp
class Node{
    public:
        int val;
        Node* next;
        Node(){
            this->val = 0;
            this->next = nullptr;
        }
        Node(int val){
            this->val = val;
            this->next = nullptr;
        }
        Node(int val, Node* next){
            this->val = val;
            this->next = next;
        }
}
```

### 1.4.1 Insertion

Logic - Traverse till the last node and then insert the new node.

```cpp
Node* insert(Node* head, int val){
    Node* newNode = new Node(val);
    if(head == nullptr){
        head = newNode;
    }else{
        Node* temp = head;
        while(temp->next != nullptr){
            temp = temp->next;
        }
        temp->next = newNode;
    }
    return head;
}
```

### 1.4.2 Deletion

Logic - Given a key find the node and delete it.

```cpp
Node* deleteNode(Node* head, int key){
    if(head == nullptr){
        return head;
    }
    if(head->val == key){
        return head->next;
    }
    Node* temp = head;
    while(temp->next != nullptr){
        if(temp->next->val == key){
            temp->next = temp->next->next;
            return head;
        }
        temp = temp->next;
    }
    return head;
}
```

### 1.4.3 Traversal

Logic - Traverse the linked list and print the values.

```cpp
void traverse(Node* head){
    Node* temp = head;
    while(temp != nullptr){
        cout<<temp->val<<" ";
        temp = temp->next;
    }
}
```

### 1.4.4 Searching

Logic - Traverse the linked list and search for the key.

```cpp
   bool search(Node* head, int key){
       Node* temp = head;
       while(temp != nullptr){
           if(temp->val == key){
               return true;
           }
           temp = temp->next;
       }
       return false;

```

## 1.5 Some tricky questions on Linked List

### 1.5.1 Reversing a Linked List

**Algorithm**:

1. Initialize three pointers `prev`, `curr` and `next` to `nullptr`, `head` and `nullptr` respectively.
2. Traverse the linked list and for each node:
   - Store the next node in `next`.
   - Set the next of the current node to `prev`.
   - Move `prev` and `curr` one step forward.
   - Move `curr` to `next`.
   - Repeat the above steps till `curr` is `nullptr`.
3. Set the head to `prev`.
4. Return the head.

```cpp
Node* reverse(Node* head){
    Node* prev = nullptr;
    Node* curr = head;
    Node* next = nullptr;
    while(curr != nullptr){
        next = curr->next;
        curr->next = prev;
        prev = curr;
        curr = next;
    }
    head = prev;
    return head;
}
```

### 1.5.2 Detecting a cycle in a Linked List

> This is also known as Floyd's Cycle Detection Algorithm or Hare and Tortoise Algorithm.
> This uses two pointers, one moving at twice the speed of the other. If there is a cycle, the two pointers will meet at some point.

**Algorithm**:

1. Initialize two pointers `slow` and `fast` to `head`.
2. Move `slow` one step and `fast` two steps.
3. If `slow` and `fast` meet at some point, there is a cycle.
4. If `fast` reaches `nullptr`, there is no cycle.

```cpp
bool hasCycle(Node* head){
    Node* slow = head;
    Node* fast = head;
    while(fast != nullptr && fast->next != nullptr){
        slow = slow->next;
        fast = fast->next->next;
        if(slow == fast){
            return true;
        }
    }
    return false;
}
```

### 1.5.3 Finding the starting point of a cycle in a Linked List

> We use the Floyd's Cycle Detection Algorithm to find the starting point of the cycle.
> Once the cycle is detected, we move one pointer to the head and move both pointers one step at a time. The point where they meet is the starting point of the cycle.

**Algorithm**:

1. Detect the cycle using Floyd's Cycle Detection Algorithm.
2. Initialize two pointers `slow` and `fast` to `head`.
3. Move `slow` one step and `fast` two steps.
4. If `slow` and `fast` meet at some point, there is a cycle.
5. Move one pointer to the head.
6. Move both pointers one step at a time.
7. The point where they meet is the starting point of the cycle.

```cpp
Node* detectCycle(Node* head){
    Node* slow = head;
    Node* fast = head;
    while(fast != nullptr && fast->next != nullptr){
        slow = slow->next;
        fast = fast->next->next;
        if(slow == fast){
            break;
        }
    }
    if(fast == nullptr || fast->next == nullptr){
        return nullptr;
    }
    slow = head;
    while(slow != fast){
        slow = slow->next;
        fast = fast->next;
    }
    return slow;
}
```

### 1.5.4 Merge k sorted linked lists

Given an array of k sorted linked lists. Merge them into a single sorted linked list.

**Algorithm**:

1. Create a min heap and insert the first element of each linked list into the heap.
2. Create a dummy head node.
3. While the heap is not empty:
   - Pop the top element from the heap.
   - Insert the popped element into the result linked list.
   - If the next element of the popped element is not null, insert it into the heap.
4. Return the head of the result linked list.

```cpp
class compare{
    public:
        bool operator()(Node* a, Node* b){
            return a->val > b->val;
        }
};

class Solution{
    public:
        Node* mergeKLists(vector<Node*>& lists){
            priority_queue<Node*, vector<Node*>, compare> pq;
            for(Node* head: lists){
                if(head != nullptr){
                    pq.push(head);
                }
            }
            Node* dummy = new Node(0);
            Node* tail = dummy;
            while(!pq.empty()){
                Node* top = pq.top();
                pq.pop();
                tail->next = top;
                tail = tail->next;
                if(top->next != nullptr){
                    pq.push(top->next);
                }
            }
            return dummy->next;
        }
};
```

### 1.5.5 Reverse a linked list in groups of k

We will be using 3 pointers to reverse the linked list in groups of k.

**Algorithm**:

1. Initialize a dummy node and point it to the head.
2. Initialize 3 pointers `prev`, `curr` and `next` to `dummy`.
3. First find the length of the linked list store it as `len`.
4. While `next` is not `nullptr`:
   - assign `curr` to `prev->next`
   - assign `next` to `curr->next`
   - have a loop counter named `limit` = `len>k?k:len-1`
   - For each `i` from 1 to `limit`:
     - assign `curr->next` to `next->next`
     - assign `next->next` to `prev->next`
     - assign `prev` to `next`
     - assign `next` to `curr->next`
   - set `prev` to `curr`
   - set `len` to `len-k`
5. Return the dummy->next.

```cpp
Node* reverseKGroup(Node* head, int k){
    Node* dummy = new Node(0);
    dummy->next = head;
    Node* prev = dummy;
    Node* curr = dummy;
    Node* next = dummy;
    int len = 0;
    while(curr != nullptr){
        len++;
        curr = curr->next;
    }
    while(next != nullptr){
        curr = prev->next;
        next = curr->next;
        for(int i=1; i<len && i<k; i++){
            curr->next = next->next;
            next->next = prev->next;
            prev->next = next;
            next = curr->next;
        }
        prev = curr;
        len -= k;
    }
    return dummy->next;
}
```

Example

```
Input: 1->2->3->4->5, k = 2
Output: 2->1->4->3->5

Input: 1->2->3->4->5, k = 3
Output: 3->2->1->4->5
```

---

# Circular Linked List

Circular linked list is a linked list where all nodes are connected to form a circle. There is no NULL at the end. A circular linked list can be a singly circular linked list or a doubly circular linked list.

**For this notes we are using a Singly Circular Linked List**

**We are assuming the following class for the Node**

```cpp
class Node*{
    public:
        int val;
        Node* next;
        Node(){
            this->val = 0;
            this->next = nullptr;
        }
        Node(int val){
            this->val = val;
            this->next = nullptr;
        }
        Node(int val, Node* next){
            this->val = val;
            this->next = next;
        }
}
```
