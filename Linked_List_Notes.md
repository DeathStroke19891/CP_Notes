# Table of Contents

| Sl. No. | Topic                                         |
| ------- | --------------------------------------------- |
| 1.      | [Linked List](#linked-list)                   |
| 2.      | [Circular Linked List](#circular-linked-list) |

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

---

| Sl. No. | Topic                                                                                                     |
| ------- | --------------------------------------------------------------------------------------------------------- |
| 2.1     | [Operations on Circular Linked Lists](#21-operations-on-circular-linked-lists)                            |
| 2.2     | [Advantages of Circular Linked List](#advantages-of-circular-linked-list)                                 |
| 2.3     | [Disadvantages of Circular Linked List](#disadvantages-of-circular-linked-list)                           |
| 2.4     | [Splitting a Circular Linked List into two halves](#213-splitting-a-circular-linked-list-into-two-halves) |

---

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

- We always get a reference to the head node.

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

## 2.1 Operations on Circular Linked Lists

Thes are the following operations that can be performed on a circular linked list:

### 2.1.1 Insertion

A node can be inserted in 3 ways to a CLL, at the beginning, at the end, and at any position.

- **Insertion at the beginning**
  - Create a new node.
  - Traverse till the last node. (last->next = head)
  - Insert the new node at the beginning. (new->next = head, last->next = new)
  - return the new head.

```cpp
Node* insertAtBeginning(Node* head, int val){
    Node* newNode = new Node(val);
    if(head == nullptr){
        newNode->next = newNode;
        return newNode;
    }
    Node* last = head;
    while(last->next != head){
        last = last->next;
    }
    newNode->next = head;
    last->next = newNode;
    return newNode;
}
```

- **Insertion at the end**
  - Create a new node.
  - Traverse till the last node. (last->next = head)
  - Insert the new node at the end. (new->next = head, last->next = new)
  - return the head.

```cpp
Node* insertAtEnd(Node* head, int val){
    Node* newNode = new Node(val);
    if(head == nullptr){
        newNode->next = newNode;
        return newNode;
    }
    Node* last = head;
    while(last->next != head){
        last = last->next;
    }
    newNode->next = head;
    last->next = newNode;
    return head;
}
```

- **Insertion at any position**
  - Create a new node.
  - Traverse till the position.
  - Make the new node point to pos->next.
  - Make the pos point to the new node.

```cpp
Node* insertAtPosition(Node* head, int val, int pos){
    Node* newNode = new Node(val);
    if(head == nullptr){
        newNode->next = newNode;
        return newNode;
    }
    Node* temp = head;
    for(int i=0; i<pos-1; i++){
        temp = temp->next;
    }
    newNode->next = temp->next;
    temp->next = newNode;
    return head;
}
```

### 2.1.2 Deletion

We can delete a node from a CLL in 3 ways, from the beginning, from the end, and from any given key.

- **Deletion from the beginning**
  - Traverse till the last node. (last->next = head)
  - Make the last node point to head->next.
  - Delete the head node.
  - return the new head.

```cpp
Node* deleteFromBeginning(Node* head){
    if(head == nullptr){
        return nullptr;
    }
    Node* last = head;
    while(last->next != head){
        last = last->next;
    }
    last->next = head->next;
    delete head;
    return last->next;
}
```

- **Deletion from the end**
  - Traverse till the last node. (last->next = head)
  - Traverse till the second last node. (temp->next != last)
  - Make the second last node point to head.
  - Delete the last node.
  - return the head.

```cpp
Node* deleteFromEnd(Node* head){
    if(head == nullptr){
        return nullptr;
    }
    Node* last = head;
    while(last->next != head){
        last = last->next;
    }
    Node* temp = head;
    while(temp->next != last){
        temp = temp->next;
    }
    temp->next = head;
    delete last;
    return head;
}
```

- **Deletion based on key**
  - Keep track of previous and current nodes.
  - Traverse till the key is found.
  - Make the previous node point to the next of the current node.
  - Delete the current node.
  - return the head.

```cpp
Node* deleteNode(Node* head, int key){
    if(head == nullptr){
        return nullptr;
    }
    Node* temp = head;
    Node* prev = nullptr;
    while(temp->val != key){
        if(temp->next == head){
            return head;
        }
        prev = temp;
        temp = temp->next;
    }
    if(temp == head){
        prev = head;
        while(prev->next != head){
            prev = prev->next;
        }
        head = head->next;
        prev->next = head;
        delete temp;
    }
    else{
        prev->next = temp->next;
        delete temp;
    }
    return head;
}
```

### Advantages of Circular Linked List

1. Any node can be a starting point.
2. Useful for applications where the last node is to be connected to the first node.
3. Useful for implementing a round-robin scheduling algorithm.
4. Circular doubly linked lists are used for implementation of advanced data structures like Fibonacci Heap.

### Disadvantages of Circular Linked List

1. Traversal is more complex than singly linked lists.
2. More complex to implement than singly linked lists.
3. More complex to delete a node than singly linked lists.
4. More complex to find the length of the linked list than singly linked lists.

### 2.1.3 Splitting a Circular Linked List into two halves

If the number of nodes in the circular linked list is odd, then make the first half one node more than the second half.
If the number of nodes in the circular linked list is even, then make the first half and the second half equal.

**Algorithm**:

1. Store the mid and last nodes of the circular linked list using `slow` and `fast` pointers.
2. Make second half circular.
3. Make first half circular.
4. Return the heads of the two

```cpp
pair<Node*, Node*> splitList(Node* head){
    if (!head || head->next == head) return {head, nullptr}; // Handle edge cases

    Node* slow = head;
    Node* fast = head;
    // Loop to find the midpoint; also works for even-length lists
    while(fast->next != head && fast->next->next != head){
        slow = slow->next;
        fast = fast->next->next;
    }

    // Adjust for even length lists
    if(fast->next->next == head){
        fast = fast->next;
    }

    Node* head1 = head;
    Node* head2 = slow->next;
    fast->next = head2; // Complete the circle for the second half
    slow->next = head1; // Complete the circle for the first half

    return {head1, head2};
}
```

---

# Doubly Linked List

This is similar to a singly linked list, but each node has a reference to the previous node as well as the next node.

**For this notes we are using a Doubly Linked List**

```cpp
class Node{
    public:
        int val;
        Node* next;
        Node* prev;
        Node(){
            this->val = 0;
            this->next = nullptr;
            this->prev = nullptr;
        }
        Node(int val){
            this->val = val;
            this->next = nullptr;
            this->prev = nullptr;
        }
        Node(int val, Node* next, Node* prev){
            this->val = val;
            this->next = next;
            this->prev = prev;
        }
};
```

## 1. Operations on Doubly Linked List

### 1.1 Insertion

1. **Insertion at the beginning**
   - Create a new node.
   - Make the new node point to the head.
   - Make the head point to the new node.
   - return the new head.

```cpp
Node* insertAtBeginning(Node* head, int val){
    Node* newNode = new Node(val);
    if(head == nullptr){
        return newNode;
    }
    newNode->next = head;
    head->prev = newNode;
    return newNode;
}
```

2. **Insertion at the end**
   - Create a new node.
   - Traverse till the last node.
   - Make the last node point to the new node.
   - Make the new node point to null.
   - return the head.

```cpp
Node* insertAtEnd(Node* head, int val){
    Node* newNode = new Node(val);
    if(head == nullptr){
        return newNode;
    }
    Node* temp = head;
    while(temp->next != nullptr){
        temp = temp->next;
    }
    temp->next = newNode;
    newNode->prev = temp;
    return head;
}
```

3. **Insertion at any position**
   - Create a new node.
   - Traverse till the position.
   - Make the new node point to pos->next.
   - Make the pos point to the new node.
   - return the head.

```cpp
Node* insertAtPosition(Node* head, int val, int pos){
    Node* newNode = new Node(val);
    if(head == nullptr){
        return newNode;
    }
    Node* temp = head;
    for(int i=0; i<pos-1; i++){
        temp = temp->next;
    }
    newNode->next = temp->next;
    temp->next->prev = newNode;
    temp->next = newNode;
    newNode->prev = temp;
    return head;
}
```

### 1.2 Deletion

1. **Deletion from the beginning**
   - Make the head point to the next node.
   - Delete the previous head.
   - return the new head.

```cpp
Node* deleteFromBeginning(Node* head){
    if(head == nullptr){
        return nullptr;
    }
    Node* temp = head;
    head = head->next;
    head->prev = nullptr;
    delete temp;
    return head;
}
```

2. **Deletion from the end**
   - Traverse till the last node.
   - Make the second last node point to null.
   - Delete the last node.
   - return the head.

```cpp
Node* deleteFromEnd(Node* head){
    if(head == nullptr){
        return nullptr;
    }
    Node* temp = head;
    while(temp->next != nullptr){
        temp = temp->next;
    }
    temp->prev->next = nullptr;
    delete temp;
    return head;
}
```

3. **Deletion based on key**
   - Keep track of previous and current nodes.
   - Traverse till the key is found.
   - Make the previous node point to the next of the current node.
   - Delete the current node.
   - return the head.

```cpp
Node* deleteNode(Node* head, int key){
    if(head == nullptr){
        return nullptr;
    }
    Node* temp = head;
    while(temp->val != key){
        temp = temp->next;
    }
    if(temp->prev != nullptr){
        temp->prev->next = temp->next;
    }
    if(temp->next != nullptr){
        temp->next->prev = temp->prev;
    }
    delete temp;
    return head;
}
```

### 1.4 Reversing a Doubly Linked List

**Algorithm**:

1. Have two pointers `curr` and `temp`.
2. Traverse the linked list and for each node:
   - Swap the next and prev pointers.
   - Move `temp` to `curr`.
   - Move `curr` to `curr->next`.
3. Return the head.

```cpp
Node* reverse(Node* head){
    Node* curr = head;
    Node* temp = nullptr;
    while(curr != nullptr){
        temp = curr->prev;
        curr->prev = curr->next;
        curr->next = temp;
        curr = curr->prev;
    }
    if(temp != nullptr){
        head = temp->prev;
    }
    return head;
}
```

We can also reverse it using recursion.

```cpp
Node* reverse(Node* head){
    if(head == nullptr || head->next == nullptr){
        return head;
    }
    Node* temp = head->next;
    head->next = head->prev;
    head->prev = temp;
    return reverse(temp);
}
```

We can also reverse it using a stack.

```cpp
Node* reverse(Node* head){
    stack<Node*> s;
    Node* temp = head;
    while(temp != nullptr){
        s.push(temp);
        temp = temp->next;
    }
    head = s.top();
    temp = head;
    s.pop();
    while(!s.empty()){
        temp->next = s.top();
        s.top()->prev = temp;
        temp = temp->next;
        s.pop();
    }
    temp->next = nullptr;
    return head;
}
```

### 1.5 List-Tree conversion

Given a binary tree , we can convert it into a doubly linked list.

**Algorithm**:

1. Convert the left subtree into a doubly linked list.
2. Convert the right subtree into a doubly linked list.
3. Make the left and right child of the root point to the left and right doubly linked lists.

```cpp
Node* treeToList(Node* root){
    if(root == nullptr){
        return nullptr;
    }
    if(root->left != nullptr){
        Node* left = treeToList(root->left);
        for(; left->next != nullptr; left = left->next);
        left->next = root;
        root->prev = left;
    }
    if(root->right != nullptr){
        Node* right = treeToList(root->right);
        for(; right->prev != nullptr; right = right->prev);
        right->prev = root;
        root->next = right;
    }
    return root;
}
```

```
Example:
Input:
        10
       /  \
      12   15
     /  \    \
    25  30   36

Output: 25<->12<->30<->10<->36<->15
```

## 2. Advantages of Doubly Linked List

1. Can be traversed in both directions.
2. Can be used to implement advanced data structures like Fibonacci Heap.
3. Can be used to implement advanced algorithms like LRU Cache.
4. Can be used to implement advanced algorithms like Deque.

## 3. Disadvantages of Doubly Linked List

1. More memory is required as compared to singly linked lists.
2. More complex to implement than singly linked lists.
3. More complex to delete a node than singly linked lists.
4. Circular doubly linked lists are more complex than singly linked lists counterparts.

---
