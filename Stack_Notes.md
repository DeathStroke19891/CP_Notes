# Table of contents

| Sl.No | Topic                               |
| ----- | ----------------------------------- |
| 1     | [Stack](#stack)                     |
| 2     | [Monotonic Stack](#monotonic-stack) |

---

# Subtopics

| Sl.No | Topic                                                |
| ----- | ---------------------------------------------------- |
| 1.1   | [Stack operations](#11-stack-operations)             |
| 1.2   | [Stack implementation](#12-stack-implementation)     |
| 1.3   | [Push operation](#push-operation)                    |
| 1.4   | [Pop operation](#pop-operation)                      |
| 1.5   | [Top operation](#top-operation)                      |
| 1.6   | [IsEmpty operation](#isempty-operation)              |
| 1.7   | [Complexity analysis](#14-complexity-analysis)       |
| 1.8   | [Applications of stack](#15-applications-of-stack)   |
| 1.9   | [Advantages of stack](#17-advantages-of-stack)       |
| 1.10  | [Disadvantages of stack](#18-disadvantages-of-stack) |

---

| Sl.No | Topic                                                        |
| ----- | ------------------------------------------------------------ |
| 2.1   | [Types of Monotonic Stack](#21-types-of-monotonic-stack)     |
| 2.2   | [Monotonic Increasing Stack](#22-monotonic-increasing-stack) |
| 2.3   | [Monotonic Decreasing Stack](#23-monotonic-decreasing-stack) |

---

## [Very very irritating variations](#peculiar-ass-problems)

| Sl.No | Topic                                                                                                                                                 |
| ----- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1     | [Designing a stack that supports getMin() in O(1) time and O(1) extra space](#1-designing-a-stack-that-supports-getmin-in-o1-time-and-o1-extra-space) |

---

## Stack

- What is Stack?
- A stack is a linear data structure that follows the principle of `Last In First Out (LIFO)`.
  Example : A stack of books.
  The last book placed on the stack is the first one to be removed.

There are two types of stack:

1. Fixed size stack
2. Dynamic size stack

## 1.1 Stack operations

There are five basic operations that can be performed on a stack:

1. Push : Add an element to the top of a stack
2. Pop : Remove an element from the top of a stack
3. Top / Peek : Return the top element of the stack without removing it
4. IsEmpty : Check if the stack is empty
5. Size : Return the number of elements in the stack (in case of fixed size stack)

## 1.2 Stack implementation

### Push operation

**Algorithm:**

1. Check if the stack is full
2. If the stack is full, return an error message
3. If the stack is not full, increment the top and add the element to the top of the stack

```cpp
void push(int element) {
    if (top == MAX_SIZE - 1) {
        cout << "Stack Overflow" << endl;
        return;
    }
    top++;
    stack[top] = element;
}
```

### Pop operation

**Algorithm:**

1. Check if the stack is empty
2. If the stack is empty, return an error message
3. If the stack is not empty, remove the element from the top of the stack and decrement the top

```cpp
void pop() {
    if (top == -1) {
        cout << "Stack Underflow" << endl;
        return;
    }
    top--;
    return;
}
```

### Top operation

**Algorithm:**

1. Check if the stack is empty
2. If the stack is empty, return an error message
3. If the stack is not empty, return the element at the top of the stack

```cpp
int topElement() {
    if (top == -1) {
        cout << "Stack is empty" << endl;
        return -1;
    }
    return stack[top];
}
```

### IsEmpty operation

**Algorithm:**

1. Check if the top is -1
2. If the top is -1, return true
3. If the top is not -1, return false

```cpp
bool isEmpty() {
    return top == -1;
}
```

- Implementing a stack using a vector in C++:

```cpp
class Stack {
private:
    vector<int> stack;
public:
    void push(int element) {
        stack.push_back(element);
    }

    void pop() {
        if (!isEmpty()) {
            stack.pop_back();
        }
    }

    int topElement() {
        if (!isEmpty()) {
            return stack.back();
        }
        return -1;
    }

    bool isEmpty() {
        return stack.empty();
    }
};
```

## 1.4 Complexity analysis

| Operation | Time Complexity | Space Complexity |
| --------- | --------------- | ---------------- |
| Push      | O(1)            | O(1)             |
| Pop       | O(1)            | O(1)             |
| Top       | O(1)            | O(1)             |
| IsEmpty   | O(1)            | O(1)             |
| Size      | O(1)            | O(1)             |

## 1.5 Applications of stack

- Stack is used in function calls and recursion.
- Stack is used in backtracking problems.
- Stack is used in parsing algorithms.
- Stack is used in expression conversion and evaluation.

## 1.7 Advantages of stack

1. It is super easy to implement and understand.
2. Highly efficient in terms of time and space complexity.
3. Follows LIFO principle which is useful in many applications such as function calls and recursion.
4. Limited memory usage as the size of the stack is fixed or dynamic.

## 1.8 Disadvantages of stack

- Limited access to elements as only the top element can be accessed.
- Potential stack overflow if the size of the stack is fixed and all the memory is used.
- No random access to elements as elements can only be added or removed from the top of the stack.

---

## Monotonic Stack

- Monotonic stack is a stack that is either mononotically increasing or monotonically decreasing.
- It is used to solve problems where we need to find the next greater or next smaller element for each element in an array.
- Monotonic stack is used to solve problems like:
  - Next Greater Element
  - Next Smaller Element
  - Largest Rectangle in Histogram
  - Sliding Window Maximum
  - Stock Span Problem
  - Maximum Area of a Circular Subarray

### 2.1 Types of Monotonic Stack

1. Monotonic Increasing Stack
2. Monotonic Decreasing Stack

### 2.2 Monotonic Increasing Stack

- In a monotonic increasing stack, the elements are arranged in increasing order from bottom to top.
- Each element added to the stack is greater than or equal to the top of the stack.
- The top of the stack contains the largest element in the stack.

**Algorithm:**

1. Initialize an empty stack.
2. Iterate through the array from left to right.
3. For each element do:
   - While the stack is not empty and the top of the stack is more than the current element, pop the stack.
4. Push the current element to the stack.

```cpp
class Solution{
public:
    stack<int> monoIncStack(vector<int>& nums) {
        stack<int> st;
        for (int i = 0; i < nums.size(); i++) {
            while (!st.empty() && st.top() > nums[i]) {
                st.pop();
            }
            st.push(nums[i]);
        }
        return st;
    }
}
```

**Time Complexity: O(n)**
**Space Complexity: O(n)**

### 2.3 Monotonic Decreasing Stack

- In a monotonic decreasing stack, the elements are arranged in decreasing order from bottom to top.
- Each element added to the stack is less than or equal to the top of the stack.
- The top of the stack contains the smallest element in the stack.
- Monotonic decreasing stack is used to solve problems like:
  - Next Smaller Element
  - Largest Rectangle in Histogram
  - Sliding Window Maximum
  - Stock Span Problem
  - Maximum Area of a Circular Subarray

**Algorithm:**

1. Initialize an empty stack.
2. Iterate through the array from left to right.
3. For each element do:
   - While the stack is not empty and the top of the stack is less than the current element, pop the stack.
4. Push the current element to the stack.

```cpp
class Solution{
public:
    stack<int> monoDecStack(vector<int>& nums) {
        stack<int> st;
        for (int i = 0; i < nums.size(); i++) {
            while (!st.empty() && st.top() < nums[i]) {
                st.pop();
            }
            st.push(nums[i]);
        }
        return st;
    }
}
```

**Time Complexity: O(n)**
**Space Complexity: O(n)**

---

## Peculiar Ass problems

### 1. Designing a stack that supports getMin() in O(1) time and O(1) extra space

> This was asked in Arcesium Interview for our classmate. He asked WTH is that.

```
Input: Consider the following SpecialStack

16  –> TOP
15
29
19
18

When getMin() is called it should return 15,
which is the minimum element in the current stack.

If we do pop two times on stack, the stack becomes

29  –> TOP
19
18

When getMin() is called, it should return 18
which is the minimum in the current stack.
```

- Approach:
  We will be writing the new minimum encountered as a function of the previous minimum already present in the stack.

Define a variable `currentMiniumum` which will store the current minimum of the stack.

We obtain problems in two steps. While pushing and popping.

**Algorithm to push**:

- Consider element = x
- if the stack is empty, push the element into the stack and `currentMinimum` = element.
- if the stack is NOT empty, compare the element to `currentMinimum`.
  - if its greater than or equal to `currentMinimum`, just push it on the stack.
  - If is less than the `currentMinimum` then we need to push `2*x - currentMinimum` on the stack and update `currentMinimum = x`.

**Algorithm to pop**:

- Remove the top element from the stack. Let it be y.
- If y is greater than or equal to `currentMinimum`, then the minimum element in the stack is still `currentMinimum`.
- If y is less than `currentMinimum`, it means we are actually popping the `currentMinimum` element. So we need to find the next minimum present in the stack.
- we had calculated the element to push as `y = 2*x - previousMinimum`. So, if we have to find the previous minimum, we can use the formula `previousMinimum = 2*x - y`.
- Now we can use this as `currentMinimum = previousMinimum`.

```cpp
class SpecialStack {
private:
    stack<int> st;
    int currentMinimum;
public:
    void push(int x) {
        if (st.empty()) {
            st.push(x);
            currentMinimum = x;
        } else {
            if (x >= currentMinimum) {
                st.push(x);
            } else {
                st.push(2*x - currentMinimum);
                currentMinimum = x;
            }
        }
            }

    void pop() {
        if (st.empty()) {
            return;
        }
        int y = st.top();
        st.pop();
        if (y < currentMinimum) {
            currentMinimum = 2*currentMinimum - y;
        }
    }

    int getMin() {
        return currentMinimum;
    }
};
```

Input: Consider the following SpecialStack

16 –> TOP
15
29
19
18

When getMin() is called it should return 15,
which is the minimum element in the current stack.

If we do pop two times on stack, the stack becomes

29 –> TOP
19
18

When getMin() is called, it should return 18
which is the minimum in the current stack.

#### There is a more sane way of doing this

We can use an auxiliary stack to store the minimum element at each level of the main stack.

```cpp
class MinStack {
public:
    stack<int> s;
    stack<int> mins;
    MinStack() {

    }

    void push(int val) {
        if(mins.empty() || mins.top()>=val){
            s.push(val);
            mins.push(val);
        }
        else
            s.push(val);
    }

    void pop() {
        if(s.top()==mins.top()){
            s.pop();
            mins.pop();
        }
        else
            s.pop();
    }

    int top() {
        return s.top();
    }

    int getMin() {
        return mins.top();
    }
};
```

This implementation uses extra space. The second stack keeps track of the minimum till that level.
We pop the `min` stack when the top of normal stack matches with `min` stack.
