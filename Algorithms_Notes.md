# Table of Contents

| Sl. No. | Topic                                                       |
| ------- | ----------------------------------------------------------- |
| 1       | [Sorting algorithms](#i-sorting-algorithms)                 |
| 2       | [Searching algorithms](#ii-searching-algorithms)            |
| 3       | [Graph and Tree algorithms](#iii-graph-and-tree-algorithms) |

---

# Subtopics

| Sl. No. | Topic                             |
| ------- | --------------------------------- |
| 1       | [Merge Sort](#1-merge-sort)       |
| 2       | [Quick Sort](#2-quick-sort)       |
| 3       | [Heap Sort](#3-heap-sort)         |
| 4       | [Counting Sort](#4-counting-sort) |
| 5       | [Radix Sort](#5-radix-sort)       |

---

# Subtopics

| Sl. No. | Topic                             |
| ------- | --------------------------------- |
| 1       | [Linear Search](#1-linear-search) |
| 2       | [Binary Search](#2-binary-search) |

---

# Subtopics

| Sl. No. | Topic                                                                                                                                           |
| ------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 1       | [Depth First Search (DFS)](#1-depth-first-search-dfs)                                                                                           |
| 2       | [Breadth First Search (BFS)](#2-breadth-first-search-bfs)                                                                                       |
| 3       | [Dijkstra's Algorithm](#3-dijkstras-algorithm)                                                                                                  |
| 4       | [Prim's Algorithm](#4-prims-algorithm)                                                                                                          |
| 5       | [Topological Sort](#5-topological-sort)                                                                                                         |
| 6       | [Lowest Common Ancestor (LCA)](#6-lowest-common-ancestor)                                                                                       |
| 7       | [Floyd-Warshall Algorithm](#7-floyd-warshall-algorithm)                                                                                         |
| 8       | [Bellman-Ford Algorithm](#8-bellman-ford-algorithm)                                                                                             |
| 9       | [Floyd-Fulkerson Algorithm](#9-floyd-fulkerson-algorithm)                                                                                       |
| 10      | [Construction of a tree from Inorder and Preorder/Postorder Traversal](#10-construction-of-a-tree-from-inorder-and-preorderpostorder-traversal) |
| 11      | [Articulation points](#11-articulation-points)                                                                                                  |
| 12      | [Bridges](#12-bridges)                                                                                                                          |
| 13      | [Lowest Common Ancestor (Tarjan's Algorithm)](#13-lowest-common-ancestor-tarjans-algorithm)                                                     |
| 14      | [Bipartite Matching](#14-bipartite-matching)                                                                                                    |

---

# I. Sorting algorithms

## 1. Merge Sort

Merge sort is the most efficient sorting algorithm. It is based on the `divide and conquer` technique. It divides the input array into two halves, calls itself for the two halves, and then merges the two sorted halves.

**Algorithm:**

1. Input: An array of N elements.
2. Output: A sorted array.
3. Divide the array into two halves.
4. Recursively sort the two halves.
5. Merge the two halves.

```cpp
// Here we will be sorting the array in ascending order.
void merge(vector<int>& arr, int left, int mid, int right){
    int n1 = mid - left + 1;
    int n2 = right - mid;
    vector<int> L(n1), R(n2);
    for(int i = 0; i < n1; i++){
        L[i] = arr[left + i];
    }
    for(int i = 0; i < n2; i++){
        R[i] = arr[mid + 1 + i];
    }
    int i = 0, j = 0, k = left;
    while(i < n1 && j < n2){
        if(L[i] <= R[j]){
            arr[k] = L[i];
            i++;
        } else {
            arr[k] = R[j];
            j++;
        }
        k++;
    }
    while(i < n1){
        arr[k] = L[i];
        i++;
        k++;
    }
    while(j < n2){
        arr[k] = R[j];
        j++;
        k++;
    }

void mergeSort(vector<int>& arr, int left, int right){
    if(left < right){
        int mid = left + (right - left) / 2;
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);
        merge(arr, left, mid, right);
    }
}
```

Time Complexity: O(NlogN)
Space Complexity: O(N) (Auxiliary space)

This algorithm is `not in-place`, i.e., it requires extra space for sorting.
This algorithm is `stable`, i.e., it preserves the order of equal elements.

We can use the same logic of merge sort to solve problems like `Merge k sorted arrays`, `merge k sorted linked lists`, etc.

| Time complexity Analysis | Value    |
| ------------------------ | -------- |
| Best Case                | O(NlogN) |
| Worst Case               | O(NlogN) |
| Average Case             | O(NlogN) |

## 2. Quick Sort

Quick sort is one of the efficient sorting algorithms. It is based on the `divide and conquer` technique. It picks an element as a pivot and partitions the given array around the picked pivot.
Next the partitioned array is sorted recursively.

**Algorithm:**

1. Input: An array of N elements.
2. Output: A sorted array.
3. Choose a pivot element.
4. Partition the array around the pivot.
5. Recursively sort the two halves.

```cpp
// Here we will be sorting the array in ascending order.
int partition(vector<int>& arr, int low, int high){
    int pivot = arr[high]; // Choosing the last element as pivot.
    int i = low - 1; // Index of smaller element.
    for(int j = low; j < high; j++){
        if(arr[j] < pivot){     // If current element is smaller than the pivot.
            i++;                // Increment the index of smaller element.
            swap(arr[i], arr[j]); // Swap the elements.
        }
    }
    swap(arr[i + 1], arr[high]); // i+1th index is the correct position of the pivot element.
    return i + 1;
}

void quickSort(vector<int>& arr, int low, int high){
    if(low < high){
        int pi = partition(arr, low, high);
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}
```

Time Complexity: O(NlogN) (Average case)
Space Complexity: O(logN) (Auxiliary space) Why? Because of the recursion stack.

This algorithm is `in-place`, i.e., it doesn't require extra space for sorting.
This algorithm is `not stable`, i.e., it doesn't preserve the order of equal elements.

We can use the same logic of quick sort to solve problems like `Kth smallest element`, `Kth largest element`, etc.

| Time complexity Analysis | Value    |
| ------------------------ | -------- |
| Best Case                | O(NlogN) |
| Worst Case               | O(N^2)   |
| Average Case             | O(NlogN) |

## 3. Heap Sort

Heap sort is one of the efficient sorting algorithms. It is based on the `heap data structure`. It first builds a max heap from the input array and then repeatedly extracts the maximum element from the heap and places it at the end of the array.
It has two main functions: `heapify` and `heapSort`.
`Heapify` is used to build a max heap from the input array.
`HeapSort` is used to sort the array.

**Algorithm:**

1. Input: An array of N elements.
2. Output: A sorted array.
3. Build a max heap from the input array.
4. Build a sorted array from the max heap by repeatedly extracting the maximum element.

```cpp
// Here we will be sorting the array in ascending order.
void heapify(vector<int>& arr, int n, int i){
    int largest = i;   // assume the largest element is at the root of the current sub-tree.
    int left = 2 * i + 1; // left child of the ith index.
    int right = 2 * i + 2; // right child of the ith index.
    if(left < n && arr[left] > arr[largest]){
        largest = left;         // If left child is greater than the largest element.
    }
    if(right < n && arr[right] > arr[largest]){
        largest = right;        // If right child is greater than the largest element.
    }
    if(largest != i){
        swap(arr[i], arr[largest]); // Swap the elements so that the largest element is at the ith index.
        heapify(arr, n, largest); // Recursively heapify the affected sub-tree.
    }
    // terminal condition : if the largest element is at the ith index.
}

void heapSort(vector<int>& arr){
    int n = arr.size();
    for(int i = n / 2 - 1; i >= 0; i--){
        heapify(arr, n, i);
    }
    for(int i = n - 1; i > 0; i--){
        swap(arr[0], arr[i]); // Move the root element to the end of the array.
        heapify(arr, i, 0); // Heapify the reduced heap.
    }
}
```

Time Complexity: O(NlogN) (Average case)
Space Complexity: O(1) (Auxiliary space)

This algorithm is `in-place`, i.e., it doesn't require extra space for sorting.
This algorithm is `not stable`, i.e., it doesn't preserve the order of equal elements.

We can use the same logic of heap sort to solve problems like `Kth smallest element`, `Kth largest element`, etc.

| Time complexity Analysis | Value    |
| ------------------------ | -------- |
| Best Case                | O(NlogN) |
| Worst Case               | O(NlogN) |
| Average Case             | O(NlogN) |

---

> the above algorithms are comparison based sorting algorithms. They are not suitable for sorting large data sets. For large data sets, we can use `radix sort`, `counting sort`, `bucket sort`, etc.

## 4. Counting Sort

Counting sort is a sorting algorithm that sorts the elements of an array by counting the number of occurrences of each unique element in the array. The count is stored in an auxiliary array and the sorted array is generated by mapping the count array.

**Algorithm:**

1. Input: An array of N elements.
2. Output: A sorted array.
3. Find the maximum element in the array.
4. Create a count array of size `max + 1` and initialize it with 0.
5. Store the count of each element in the count array.
6. Find the cumulative sum of the count array.
7. Write the elements into the output array from the end of the count array.

```cpp
// Here we will be sorting the array in ascending order.
void countingSort(vector<int>& arr){
    int n = arr.size();
    int max = *max_element(arr.begin(), arr.end());
    vector<int> count(max + 1, 0);
    vector<int> output(n);
    for(int i = 0; i < n; i++){
        count[arr[i]]++;
    }
    for(int i = 1; i <= max; i++){
        count[i] += count[i - 1];
    }
    for(int i = n - 1; i >= 0; i--){
        output[count[arr[i]] - 1] = arr[i];
        count[arr[i]]--;
    }
    for(int i = 0; i < n; i++){
        arr[i] = output[i];
    }
}
```

Time Complexity: O(N + K) (Average case)
Space Complexity: O(N + K) (Auxiliary space)

This algorithm is `not in-place`, i.e., it requires extra space for sorting.
This algorithm is `stable`, i.e., it preserves the order of equal elements.

We can use the same logic of counting sort to solve problems like `sort an array of 0s, 1s, and 2s`, `sort an array of 0s, 1s, 2s, and 3s`, etc.

| Time complexity Analysis | Value    |
| ------------------------ | -------- |
| Best Case                | O(N + K) |
| Worst Case               | O(N + K) |
| Average Case             | O(N + K) |

## 5. Radix Sort

Radix sort is a non-comparative sorting algorithm. It sorts the elements by first grouping the individual digits of the same place value and sorting them according to that order. It is based on the `counting sort` algorithm.

**Algorithm:**

1. Input: An array of N elements.
2. Output: A sorted array.
3. Make each number to have the same number of digits by adding leading zeros.
4. Initialize queue for each digit from 0 to 9.
5. For each digit from the least significant digit to the most significant digit, do the following:
   - Enqueue the elements into the respective queue based on the digit.
   - Dequeue the elements from the queue and store them back into the array.
6. The array is sorted.

```cpp
// Here we will be sorting the array in ascending order.
void radixSort(vector<int>& arr){
    int max = *max_element(arr.begin(), arr.end());
    // add leading zeros to make each number to have the same number of digits.
    int digits = 0;
    while(max > 0){
        digits++;
        max /= 10;
    }
    for(int i = 0; i < digits; i++){
        vector<queue<int>> q(10);
        for(int j = 0; j < arr.size(); j++){
            int digit = (arr[j] / int(pow(10, i))) % 10;
            q[digit].push(arr[j]);
        }
        int k = 0;
        for(int j = 0; j < 10; j++){
            while(!q[j].empty()){
                arr[k++] = q[j].front();
                q[j].pop();
            }
        }
    }
}
```

Time Complexity: O(N \* K) (Average case)
Space Complexity: O(N + K) (Auxiliary space)

This algorithm is `not in-place`, i.e., it requires extra space for sorting.
This algorithm is `stable`, i.e., it preserves the order of equal elements.

We can use the same logic of radix sort to solve problems like `sort an array of strings`, `sort an array of dates`, etc.

| Time complexity Analysis | Value     |
| ------------------------ | --------- |
| Best Case                | O(N \* K) |
| Worst Case               | O(N \* K) |
| Average Case             | O(N \* K) |

---

# II. Searching algorithms

We have the following searching algorithms mainly:

1. Linear Search
2. Binary Search

## 1. Linear Search

Given an array of N elements, the linear search algorithm searches for a given element in the array by iterating through each element of the array.

**Algorithm:**

1. Input: An array of N elements and a key element.
2. Output: The index of the key element if found, else -1.
3. Iterate through each element of the array.
4. If the current element is equal to the key element, return the index.
5. If the key element is not found, return -1.

```cpp
int linearSearch(vector<int>& arr, int key){
    for(int i = 0; i < arr.size(); i++){
        if(arr[i] == key){
            return i;
        }
    }
    return -1;
}
```

Time Complexity: O(N)
Space Complexity: O(1)

This algorithm can be used to solve problems like `find the first occurrence of an element`, `find the last occurrence of an element`, etc.

| Time complexity Analysis | Value |
| ------------------------ | ----- |
| Best Case                | O(1)  |
| Worst Case               | O(N)  |
| Average Case             | O(N)  |

## 2. Binary Search

Here we are using divide and conquer technique to search for an element in a sorted array.
Iteratively divide the array into two halves and search for the element in the left half if the element is less than the middle element, else search in the right half.

> Pre-requisite: The array should be sorted.

**Algorithm:**

1. Input: A sorted array of N elements and a key element.
2. Output: The index of the key element if found, else -1.
3. Initialize low = 0 and high = N - 1.
4. Repeat the following steps until low <= high:
   - Calculate mid = (low + high) / 2.
   - If the key element is equal to the middle element, return mid.
   - If the key element is less than the middle element, set high = mid - 1.
   - If the key element is greater than the middle element, set low = mid + 1.

```cpp
int binarySearch(vector<int>& arr, int key){
    int low = 0, high = arr.size() - 1;
    while(low <= high){
        int mid = low + (high - low) / 2;
        if(arr[mid] == key){
            return mid;
        } else if(arr[mid] < key){
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }
    return -1;
}
```

Time Complexity: O(logN)
Space Complexity: O(1)

This algorithm can be used to solve problems like `find the first occurrence of an element`, `find the last occurrence of an element`, etc.

| Time complexity Analysis | Value   |
| ------------------------ | ------- |
| Best Case                | O(1)    |
| Worst Case               | O(logN) |
| Average Case             | O(logN) |

This algorithm has different implementations like `recursive binary search`, `lower bound binary search`, `upper bound binary search`, etc.

### Recursive Binary Search

```cpp
int binarySearch(vector<int>& arr, int low, int high, int key){
    if(low <= high){
        int mid = low + (high - low) / 2;
        if(arr[mid] == key){
            return mid;
        } else if(arr[mid] < key){
            return binarySearch(arr, mid + 1, high, key);
        } else {
            return binarySearch(arr, low, mid - 1, key);
        }
    }
    return -1;
}
```

### Lower Bound Binary Search

```cpp
// This calculates the lower bound of the key element. ie the first occurrence of the key element.
int lowerBound(vector<int>& arr, int key){
    int low = 0, high = arr.size() - 1;
    while(low < high){
        int mid = low + (high - low) / 2;
        if(arr[mid] < key){
            low = mid + 1;
        } else {
            high = mid;
        }
    }
    return low;
}
```

```
Example:
arr = [1, 2, 3, 4, 4, 4, 5, 6]
key = 4
Output: 3
Dry run :
1. low = 0, high = 7, mid = 3, arr[mid] = 4, low = 0, high = 3
2. low = 0, high = 3, mid = 1, arr[mid] = 2, low = 2, high = 3
3. low = 2, high = 3, mid = 2, arr[mid] = 3, low = 3, high = 3
4. Breaks out of the loop and returns low = 3.
```

### Upper Bound Binary Search

```cpp
// This calculates the upper bound of the key element. ie the last occurrence of the key element.
int upperBound(vector<int>& arr, int key){
    int low = 0, high = arr.size() - 1;
    while(low < high){
        int mid = low + (high - low) / 2;
        if(arr[mid] <= key){
            low = mid + 1;
        } else {
            high = mid;
        }
    }
    return low;
}
```

```
Example:
arr = [1, 2, 3, 4, 4, 4, 5, 6]
key = 4
Output: 6
Dry run :
1. low = 0, high = 7, mid = 3, arr[mid] = 4, low = 4, high = 7
2. low = 4, high = 7, mid = 5, arr[mid] = 4, low = 5, high = 7
3. low = 5, high = 7, mid = 6, arr[mid] = 5, low = 5, high = 6
4. low = 5, high = 6, mid = 5, arr[mid] = 4, low = 6, high = 6
5. Breaks out of the loop and returns low = 6.

Returns the index of the next element after the last occurrence of the key element.
```

### Searching in a rotated sorted array

A rotated sorted array is an array that is sorted and then rotated at some pivot element. We can use the following algorithm to search for an element in a rotated sorted array.

```
Example:
arr = [1,2,3,4,5,6]
rotated_arr = [4,5,6,1,2,3]
```

**Algorithm:**

1. Input: A rotated sorted array of N elements and a key element.
2. Output: The index of the key element if found, else -1.
3. Initialize low = 0 and high = N - 1.
4. Repeat the following steps until low <= high:
   - Calculate mid = (low + high) / 2.
   - If the key element is equal to the middle element, return mid.
   - If the left half is sorted and the key element is in the left half, set high = mid - 1.
   - If the right half is sorted and the key element is in the right half, set low = mid + 1.
   - If the left half is sorted and the key element is in the right half, set low = mid + 1.
   - If the right half is sorted and the key element is in the left half, set high = mid - 1.

```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int left = 0;
        int right = nums.size() - 1;

        while (left <= right) {
            int mid = (left + right) / 2;

            if (nums[mid] == target) {
                return mid;
            }
            else if (nums[mid] >= nums[left]) { // Left half is in sorted order
                if (nums[left] <= target && target <= nums[mid]) { // target is present in that left half
                    right = mid - 1;
                } else {
                    left = mid + 1;
                }
            }
            else {  // Right half is in sorted order
                if (nums[mid] <= target && target <= nums[right]) {  // target is present in that right half
                    left = mid + 1;
                } else {
                    right = mid - 1;
                }
            }
        }

        return -1;
    }
};
```

The intuition behind this problem is that we need to find which half is sorted and then check if the target element is present in that half. If it is present, then we can search in that half, else we can search in the other half.

> here is a leetcode soultion explained with extensive comments. [Link](https://leetcode.com/problems/search-in-rotated-sorted-array/solutions/5378208/video-find-a-sorted-part-in-ascending-order)

---

# III. Graph and Tree algorithms

Trees are a subset of graphs. Trees are acyclic graphs. We have the following tree algorithms mainly:

1. Depth First Search (DFS)
2. Breadth First Search (BFS)
3. Dijkstra's Algorithm
4. Prim's Algorithm
5. Topological Sort
6. Lowest Common Ancestor (LCA)
7. Floyd-Warshall Algorithm
8. Bellman-Ford Algorithm
9. Floyd-Fulkerson Algorithm
10. Construction of a tree from Inorder and Preorder/Postorder Traversal
11. Articulation points
12. Bridges
13. Lowest Common Ancestor (Tarjan's Algorithm)
14. Bipartite Matching

We will assume that the following is the strcuture of the tree:

```cpp
 struct TreeNode {
     int val;
     TreeNode *left;
     TreeNode *right;
     TreeNode() : val(0), left(nullptr), right(nullptr) {}
     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 };
```

## 1. Depth First Search (DFS)

Depth first search is a traversal algorithm used to traverse the nodes of a graph or tree. It starts from the root node and explores as far as possible along each branch before backtracking.

> Tree implementation

```cpp
// This is the pre-order traversal of the tree.
void dfs(TreeNode* root){
    if(root == nullptr){
        return;
    }
    cout << root->val << " ";
    dfs(root->left);
    dfs(root->right);
}

// Similarly we can implement the in-order and post-order traversal of the tree.
// In-order traversal
void dfs(TreeNode* root){
    if(root == nullptr){
        return;
    }
    dfs(root->left);
    cout << root->val << " ";
    dfs(root->right);
}
// Post-order traversal
void dfs(TreeNode* root){
    if(root == nullptr){
        return;
    }
    dfs(root->left);
    dfs(root->right);
    cout << root->val << " ";
}
```

| Time complexity Analysis | Value |
| ------------------------ | ----- |
| Best Case                | O(N)  |
| Worst Case               | O(N)  |
| Average Case             | O(N)  |

> Graph implementation

The adjacency list representation of the graph is used here.

```cpp
// Adjacency list representation of the graph.
class Graph {
    int V;
    vector<vector<int>> adj;
    Graph(int V){
        this->V = V;
        adj.resize(V);
    }
};
```

```cpp
// This is the recursive implementation of the depth first search algorithm.
class Solution {
    public:
    void dfs(int node, vector<vector<int>>& adj, vector<bool>& visited){
        visited[node] = true;
        cout << node << " ";
        for(auto it : adj[node]){
            if(!visited[it]){
                dfs(it, adj, visited);
            }
        }
    }
    int main(){
        int n, m;
        cin >> n >> m;
        vector<vector<int>> adj(n);
        for(int i = 0; i < m; i++){
            int u, v;
            cin >> u >> v;
            adj[u].push_back(v);
            adj[v].push_back(u);
        }
        vector<bool> visited(n, false);
        for(int i = 0; i < n; i++){
            if(!visited[i]){
                dfs(i, adj, visited);
            }
        }
        return 0;
    }
};
```

| Time complexity Analysis | Value  |
| ------------------------ | ------ |
| Best Case                | O(V+E) |
| Worst Case               | O(V+E) |
| Average Case             | O(V+E) |

Note - This is for the adjacency list representation of the graph.

| Time complexity Analysis | Value  |
| ------------------------ | ------ |
| Best Case                | O(N^2) |
| Worst Case               | O(N^2) |
| Average Case             | O(N^2) |

Note - This is for the adjacency matrix representation of the graph.

## 2. Breadth First Search (BFS)

Breadth first search is a traversal algorithm used to traverse the nodes of a graph or tree. It starts from the root node and explores all the nodes at the present depth before moving on to the nodes at the next depth.

> Tree implementation

```cpp
// This is the level-order traversal of the tree.
void bfs(TreeNode* root){
    if(root == nullptr){
        return;
    }
    queue<TreeNode*> q;
    q.push(root);
    while(!q.empty()){
        TreeNode* node = q.front();
        q.pop();
        cout << node->val << " ";
        if(node->left != nullptr){
            q.push(node->left);
        }
        if(node->right != nullptr){
            q.push(node->right);
        }
    }
}
```

| Time complexity Analysis | Value |
| ------------------------ | ----- |
| Best Case                | O(N)  |
| Worst Case               | O(N)  |
| Average Case             | O(N)  |

> Graph implementation

The adjacency list representation of the graph is used here.

```cpp
void bfs(int node, vector<vector<int>>& adj, vector<bool>& visited){
    queue<int> q;
    q.push(node);
    visited[node] = true;
    while(!q.empty()){
        int node = q.front();
        q.pop();
        cout << node << " ";
        for(auto it : adj[node]){
            if(!visited[it]){
                visited[it] = true;
                q.push(it);
            }
        }
    }
}
```

| Time complexity Analysis | Value  |
| ------------------------ | ------ |
| Best Case                | O(V+E) |
| Worst Case               | O(V+E) |
| Average Case             | O(V+E) |

Note - This is for the adjacency list representation of the graph.

| Time complexity Analysis | Value  |
| ------------------------ | ------ |
| Best Case                | O(N^2) |
| Worst Case               | O(N^2) |
| Average Case             | O(N^2) |

Note - This is for the adjacency matrix representation of the graph.

## 3 Dijkstra's Algorithm

Dijkstra's algorithm is a shortest path algorithm used to find the shortest path from a source node to all other nodes in a graph.
This is an example of a greedy algorithm.

> Graph Implementation

**Algorithm:**

1. Input: A graph with N nodes and E edges, and a source node.
2. Output: The shortest path from the source node to all other nodes.
3. Initialize a distance array with infinity and the source node with 0.
4. Initialize a priority queue and push the source node with distance 0.
5. Repeat the following steps until the priority queue is empty:
   - Extract the node with the minimum distance from the priority queue.
   - For each neighbor of the extracted node, do the following:
     - If the distance of the neighbor is greater than the distance of the extracted node + the edge weight, update the distance of the neighbor.
     - Push the neighbor into the priority queue with the updated distance.

```cpp
class Solution {
    public:
    void dijkstra(int src, vector<vector<pair<int, int>>>& adj, int V){
        vector<int> dist(V, INT_MAX);
        dist[src] = 0;
        priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> pq;
        pq.push({0, src});
        while(!pq.empty()){
            int node = pq.top().second;
            int node_dist = pq.top().first;
            pq.pop();
            for(auto it : adj[node]){ // it = {node, weight}
                if(node_dist + it.second < dist[it.first]){
                    dist[it.first] = node_dist + it.second;
                    pq.push({dist[it.first], it.first});
                }
            }
        }
        for(int i = 0; i < V; i++){
            cout << dist[i] << " ";
        }
    }
    int main(){
        int n, m;
        cin >> n >> m;
        vector<vector<pair<int, int>>> adj(n);
        for(int i = 0; i < m; i++){
            int u, v, wt;
            cin >> u >> v >> wt;
            adj[u].push_back({v, wt});
        }
        int src;
        cin >> src;
        dijkstra(src, adj, n);
        return 0;
    }
};
```

| Time complexity Analysis | Value  |
| ------------------------ | ------ |
| Best Case                | O(V+E) |
| Worst Case               | O(V+E) |
| Average Case             | O(V+E) |

```
// Here priority queue does the job of visited array.


Dry run:
Example:
Graph representation (each edge is represented as {vertex, weight}):

Vertex 0: {1, 4}, {2, 1}
Vertex 1: {3, 1}
Vertex 2: {1, 2}, {3, 5}
Vertex 3: {4, 3}
Vertex 4: No outgoing edges
We want to find the shortest path from vertex 0 to all other vertices.

Initialization
Distances: dist[0, ∞, ∞, ∞, ∞] (distance to itself is 0, others are infinity)
Visited: [false, false, false, false, false]
Source: src = 0

Step 1: Visit Vertex 0
Update distances using vertex 0's edges:
dist[1] = 4 (0 → 1)
dist[2] = 1 (0 → 2)
Visited[0] = true

Step 2: Visit Vertex 2 (smallest distance among unvisited)
Update distances using vertex 2's edges:
dist[1] = min(4, 1 + 2) = 3 (0 → 2 → 1)
dist[3] = min(∞, 1 + 5) = 6 (0 → 2 → 3)
Visited[2] = true

Step 3: Visit Vertex 1 (next smallest distance)
Update distances using vertex 1's edges:
dist[3] = min(6, 3 + 1) = 4 (0 → 2 → 1 → 3)
Visited[1] = true

Step 4: Visit Vertex 3 (next smallest distance)
Update distances using vertex 3's edges:
dist[4] = min(∞, 4 + 3) = 7 (0 → 2 → 1 → 3 → 4)
Visited[3] = true

Step 5: Visit Vertex 4
No outgoing edges to update distances.
Visited[4] = true

Final Distances
From vertex 0 to:
Vertex 1: Distance = 3
Vertex 2: Distance = 1
Vertex 3: Distance = 4
Vertex 4: Distance = 7
```

> Tree implementation

```cpp
// This is the implementation of the dijkstra's algorithm for a tree.
void dijkstra(TreeNode* root){
    if(root == nullptr){
        return;
    }
    priority_queue<pair<int, TreeNode*>, vector<pair<int, TreeNode*>>, greater<pair<int, TreeNode*>>> pq;
    pq.push({0, root});
    while(!pq.empty()){
        TreeNode* node = pq.top().second;
        int node_dist = pq.top().first;
        pq.pop();
        cout << node->val << " ";
        if(node->left != nullptr){
            pq.push({node_dist + 1, node->left});
        }
        if(node->right != nullptr){
            pq.push({node_dist + 1, node->right});
        }
    }
}
```

## 4. Prim's Algorithm

> This is for Minimum Spanning Tree

Prims algorithm is a minimum spanning tree algorithm used to find the minimum spanning tree of a graph. It starts from an arbitrary node and adds the minimum weight edge to the tree at each step.

What is a minimum spanning tree?
A minimum spanning tree is a subset of the edges of a connected, edge-weighted graph that connects all the vertices together with the minimum possible total edge weight.
In simple terms, it is a tree that connects all the vertices of the graph with the minimum possible total edge weight.

> Graph Implementation

**Algorithm:**

1. Input: A graph with N nodes and E edges.
2. Output: The minimum spanning tree of the graph.
3. Choose an arbitrary node as the starting node of MST.
4. Till there are vertices which are not included in the MST, do the following:
   - Find the minimum weight edge from the vertices included in the MST to the vertices not included in the MST.
   - Add the minimum weight edge to the MST.

```cpp
// We take the adjacency list representation of the graph.
class Solution {
    public:
    void prims(int src, vector<vector<pair<int, int>>>& adj, int V){
        vector<int> key(V, INT_MAX);
        vector<int> parent(V, -1);
        vector<bool> mst(V, false);
        priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> pq;
        pq.push({0, src});
        key[src] = 0;
        while(!pq.empty()){
            int u = pq.top().second;
            pq.pop();
            mst[u] = true;
            for(auto it : adj[u]){
                int v = it.first;
                int weight = it.second;
                if(mst[v] == false && weight < key[v]){
                    parent[v] = u;
                    key[v] = weight;
                    pq.push({key[v], v});
                }
            }
        }
        for(int i = 1; i < V; i++){
            cout << parent[i] << " - " << i << " " << key[i] << endl;
        }
    }
    int main(){
        int n, m;
        cin >> n >> m;
        vector<vector<pair<int, int>>> adj(n);
        for(int i = 0; i < m; i++){
            int u, v, wt;
            cin >> u >> v >> wt;
            adj[u].push_back({v, wt});
            adj[v].push_back({u, wt});
        }
        prims(0, adj, n);
        return 0;
    }
};
```

| Time complexity Analysis | Value  |
| ------------------------ | ------ |
| Best Case                | O(V+E) |
| Worst Case               | O(V+E) |
| Average Case             | O(V+E) |

The key array is used to store the minimum weight edge from the vertices included in the MST to the vertices not included in the MST.
Hence it is initialized with INT_MAX.

The parent array is used to store the parent of each vertex in the MST.
Here -1 is used to represent that the vertex is not included in the MST.

The mst array is used to store whether the vertex is included in the MST or not.

First we push the source node with distance 0 into the priority queue.
Then we extract the node with the minimum distance from the priority queue.
For first run it will be the source node.
Then we mark the node as included in the MST.
Then we iterate through the neighbors of the extracted node.
Push each neighbor into the priority queue if it is not included in the MST and the weight is less than the key of the neighbor.

This means that , the given neighbour can be reached from the extracted node with the minimum weight edge whose weight is less than the key of the neighbour.

We can also use adjacency weight matrix representation of the graph.

```cpp
class Solution {
    public:
    void prims(int src, vector<vector<int>>& adj, int V){
        vector<int> key(V, INT_MAX);
        vector<int> parent(V, -1);
        vector<bool> mst(V, false);
        priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> pq;
        pq.push({0, src});
        key[src] = 0;
        while(!pq.empty()){
            int u = pq.top().second;
            pq.pop();
            mst[u] = true;
            for(int v = 0; v < V; v++){
                if(adj[u][v] != 0 && mst[v] == false && adj[u][v] < key[v]){
                    parent[v] = u;
                    key[v] = adj[u][v];
                    pq.push({key[v], v});
                }
            }
        }
        for(int i = 1; i < V; i++){
            cout << parent[i] << " - " << i << " " << key[i] << endl;
        }
    }
    int main(){
        int n, m;
        cin >> n >> m;
        vector<vector<int>> adj(n, vector<int>(n, 0));
        for(int i = 0; i < m; i++){
            int u, v, wt;
            cin >> u >> v >> wt;
            adj[u][v] = wt;
            adj[v][u] = wt;
        }
        prims(0, adj, n);
        return 0;
    }
};
```

| Time complexity Analysis | Value  |
| ------------------------ | ------ |
| Best Case                | O(V^2) |
| Worst Case               | O(V^2) |
| Average Case             | O(V^2) |

## 5. Topological Sort

Topological sort is an ordering of the vertices of a directed acyclic graph (DAG) such that for every directed edge from vertex u to vertex v, u comes before v in the ordering.

> Graph Implementation

**Algorithm:**

1. Input: A graph with N nodes and E edges.
2. Output: The topological ordering of the graph.
3. Initialize an indegree array with 0.
4. Calculate the indegree of each node.
5. Initialize a queue and push the nodes with indegree 0 into the queue.
6. Repeat the following steps until the queue is empty:
   - Extract the node from the queue.
   - For each neighbor of the extracted node, do the following:
     - Decrement the indegree of the neighbor.
     - If the indegree of the neighbor is 0, push it into the queue.

```cpp
class Solution{
    public:
        // Graph is represented as adjacency matrix
        void topologicalSort(vector<vector<int>>& adj, int V){
            vector<int> indegree(V, 0);
            for(int i = 0; i < V; i++){
                for(int j = 0; j < V; j++){
                    if(adj[i][j] == 1){
                        indegree[j]++;
                    }
                }
            }
            queue<int> q;
            for(int i = 0; i < V; i++){
                if(indegree[i] == 0){
                    q.push(i);
                }
            }
            while(!q.empty()){
                int node = q.front();
                q.pop();
                cout << node << " ";
                for(int i = 0; i < V; i++){
                    if(adj[node][i] == 1){
                        indegree[i]--;
                        if(indegree[i] == 0){
                            q.push(i);
                        }
                    }
                }
            }
        }
}
```

There is also a adjacency list representation of the graph.

```cpp
class Solution{
    public:
        void topologicalSort(vector<vector<int>>adj, int V){
            vector<int> indegree(V, 0);
            for(int i = 0; i < V; i++){
                for(auto it : adj[i]){
                    indegree[it]++;
                }
            }
            queue<int> q;
            for(int i = 0; i < V; i++){
                if(indegree[i] == 0){
                    q.push(i);
                }
            }
            while(!q.empty()){
                int node = q.front();
                q.pop();
                cout << node << " ";
                for(auto it : adj[node]){
                    indegree[it]--;
                    if(indegree[it] == 0){
                        q.push(it);
                    }
                }
            }
        }
}
```

| Time complexity Analysis | Value  |
| ------------------------ | ------ |
| Adjacency List           | -      |
| Best Case                | O(V+E) |
| Worst Case               | O(V+E) |
| Average Case             | O(V+E) |
| Adjacency Matrix         | -      |
| Best Case                | O(V^2) |
| Worst Case               | O(V^2) |
| Average Case             | O(V^2) |

## 6. Lowest Common Ancestor (LCA)

This is used to find the lowest common ancestor of two nodes in a binary tree.

**Algorithm:**

1. Input: A binary tree and two nodes.
2. Output: The lowest common ancestor of the two nodes.
3. If the root is null, return null.
4. If the root is equal to either of the nodes, return the root.
   - We assume that a given node can be an ancestor of itself.
5. Recursively find the LCA in the left subtree and right subtree.
6. If both the left and right subtrees return a non-null value, then the root is the LCA.

```cpp
class Solution {
    public:
    TreeNode* lca(TreeNode* root, TreeNode* p, TreeNode* q){
        if(root == nullptr){
            return nullptr;
        }
        if(root == p || root == q){
            return root;
        }
        TreeNode* left = lca(root->left, p, q);
        TreeNode* right = lca(root->right, p, q);
        if(left != nullptr && right != nullptr){
            return root;
        }
        if(left != nullptr){
            return left;
        }
        return right;
    }
};
```

| Time complexity Analysis | Value |
| ------------------------ | ----- |
| Best Case                | O(N)  |
| Worst Case               | O(N)  |
| Average Case             | O(N)  |

Why its O(N) ?
In the worst case, we may have to visit all the nodes of the binary tree to find the LCA.
In the best case, we may find the LCA in the first few nodes itself.

## 7. Floyd-Warshall Algorithm

Floyd Warshall algorithm is an all-pairs shortest path algorithm used to find the shortest path between all pairs of vertices in a graph.

**Algorithm:**

1. Input: A graph with N nodes and E edges.
2. Output: The shortest path between all pairs of vertices.
3. Initialize a distance matrix with infinity.
4. Initialize the diagonal of the distance matrix with 0.
5. For each edge in the graph, update the distance matrix with the edge weight.
6. Repeat the following steps for each vertex as an intermediate vertex:
   - For each pair of vertices, do the following:
     - If the distance between the pair of vertices is greater than the sum of the distance between the pair of vertices through the intermediate vertex, update the distance.

```cpp
class Solution{
    public:
    vector<vector<int>> floydWarshall(vector<vector<int>>& graph, int V){
        vector<vector<int>> dist = graph;
        for(int k = 0; k < V; k++){
            for(int i = 0; i < V; i++){
                for(int j = 0; j < V; j++){
                    if(dist[i][k] != INT_MAX && dist[k][j] != INT_MAX && dist[i][k] + dist[k][j] < dist[i][j]){
                        dist[i][j] = dist[i][k] + dist[k][j];
                    }
                }
            }
        }
        return dist;
    }
}
```

| Time complexity Analysis | Value  |
| ------------------------ | ------ |
| Best Case                | O(V^3) |
| Worst Case               | O(V^3) |
| Average Case             | O(V^3) |

There is also a adjacency list representation of the graph.

```cpp
class Solution{
    public:
    vector<vector<int>> floydWarshall(vector<vector<pair<int, int>>>& adj, int V){
        vector<vector<int>> dist(V, vector<int>(V, INT_MAX));
        for(int i = 0; i < V; i++){
            dist[i][i] = 0;
            for(auto it : adj[i]){
                dist[i][it.first] = it.second;
            }
        }
        for(int k = 0; k < V; k++){
            for(int i = 0; i < V; i++){
                for(int j = 0; j < V; j++){
                    if(dist[i][k] != INT_MAX && dist[k][j] != INT_MAX && dist[i][k] + dist[k][j] < dist[i][j]){
                        dist[i][j] = dist[i][k] + dist[k][j];
                    }
                }
            }
        }
        return dist;
    }
}
```

| Time complexity Analysis | Value  |
| ------------------------ | ------ |
| Best Case                | O(V^3) |
| Worst Case               | O(V^3) |
| Average Case             | O(V^3) |

Floyd Warshall is best suited for dense graphs.

## 8. Bellman-Ford Algorithm

This is a single source shortest path algorithm used to find the shortest path from a source node to all other nodes in a graph.

> This works for graphs with negative edge weights.

**Algorithm:**

1. Input: A graph with N nodes and E edges, and a source node.
2. Output: The shortest path from the source node to all other nodes.
3. Initialize a distance array with infinity and the source node with 0.
4. Repeat the following steps for V-1 times:
   - For each edge in the graph, do the following:
     - If the distance of the destination node is greater than the distance of the source node + the edge weight, update the distance of the destination node.
5. Check for negative weight cycles.
6. If there are no negative weight cycles, return the distance array.

```cpp
class Solution{
    public:
    vector<int> bellmanFord(int src, vector<vector<int>>& edges, int V){
        /*
        structure of graphs is {u, v, wt}
        */
        vector<int> dist(V, INT_MAX);
        dist[src] = 0;
        for(int i = 0; i < V-1; i++){
            for(auto edge : edges){
                int u = edge[0];
                int v = edge[1];
                int wt = edge[2];
                if(dist[u] != INT_MAX && dist[u] + wt < dist[v]){
                    dist[v] = dist[u] + wt;
                }
            }
        }
        for(auto edge : edges){
            int u = edge[0];
            int v = edge[1];
            int wt = edge[2];
            if(dist[u] != INT_MAX && dist[u] + wt < dist[v]){
                cout << "Negative weight cycle found!";
                break;
            }
        }
        return dist;
    }
}
```

| Time complexity Analysis | Value |
| ------------------------ | ----- |
| Best Case                | O(V)  |
| Worst Case               | O(VE) |
| Average Case             | O(VE) |

Best case is when the graph is already sorted and we need to just iterate through the vertices.
Sorted means the graph is already in the order of the shortest path.

Worst case is when we need to iterate through all the edges for V-1 times.

What is a negetive weight cycle ?
A negetive weight cycle is a cycle in the graph where the sum of the weights of the edges in the cycle is negative.

How make sure that there is no negative weight cycle ?
If there is no negative weight cycle, then the shortest path from the source node to all other nodes will be found in V-1 iterations.
If there is a negative weight cycle, then the shortest path will not be found in V-1 iterations.

So in the distance array if we find that the distance of the destination node is greater than the distance of the source node + the edge weight, then it means that there is a negative weight cycle.

Handling disconnected graphs:
If the graph is disconnected, then we need to run the Bellman-Ford algorithm for each connected component of the graph.

## 9. Floyd-Fulkerson Algorithm

Flow networks are used to represent the flow of a commodity from one node to another in a graph. The Floyd-Fulkerson algorithm is used to find the maximum flow in a flow network.

**Algorithm:**

1. Input: A flow network with N nodes and E edges, a source node, and a sink node.
2. Output: The maximum flow from the source node to the sink node.
3. Start with the flow as 0.
4. Repeat the following steps until there is a path from the source node to the sink node:
   - Find a path from the source node to the sink node.
   - Find the minimum capacity of the path.
   - Update the flow of the path.
   - Update the residual graph.
5. Return the maximum flow.

```cpp
class Solution{
    public:
    bool bfs(vector<vector<int>>& rGraph, int src, int dest, vector<int>& parent, int V){
        vector<bool> visited(V, false);
        queue<int> q;
        q.push(src);
        visited[src] = true;
        parent[src] = -1;
        while(!q.empty()){
            int u = q.front();
            q.pop();
            for(int v = 0; v < V; v++){
                if(visited[v] == false && rGraph[u][v] > 0){
                    q.push(v);
                    parent[v] = u;
                    visited[v] = true;
                }
            }
        }
        return visited[dest];
    }
    int fordFulkerson(vector<vector<int>>& graph, int src, int dest, int V){
        // graph structure is graph[u][v] = capacity  of edge from u to v
        vector<vector<int>> rGraph = graph;
        vector<int> parent(V);
        int maxFlow = 0;
        while(bfs(rGraph, src, dest, parent, V)){
            int pathFlow = INT_MAX;
            for(int v = dest; v != src; v = parent[v]){
                int u = parent[v];
                pathFlow = min(pathFlow, rGraph[u][v]);
            }
            for(int v = dest; v != src; v = parent[v]){
                int u = parent[v];
                rGraph[u][v] -= pathFlow;
                rGraph[v][u] += pathFlow;
            }
            maxFlow += pathFlow;
        }
        return maxFlow;
    }
}
```

The code is doing the following:

1. It is finding the path from the source node to the sink node using BFS.
2. It is finding the minimum capacity of the path.
3. It is updating the flow of the path.
4. It is updating the residual graph.
5. It is returning the maximum flow.

BFS is doing the following:

1. It takes the residual graph, source node, sink node, parent array, and the number of nodes as input.
2. It initializes a visited array with false and a queue.
3. It pushes the source node into the queue and marks it as visited.
4. It iterates through the neighbors of the source node.
5. If the neighbor is not visited and the capacity of the edge is greater than 0, it pushes the neighbor into the queue and marks it as visited.
6. It returns whether the sink node is visited or not.
7. If the sink node is visited, it means there is a path from the source node to the sink node.
8. If there is a path, it finds the minimum capacity of the path.

This is because we are using adjacency matrix representation of the graph.
| Time complexity Analysis | Value |
| ------------------------ | -------- |
| Best Case | O(E V^3) |
| Worst Case | O(E V^3) |
| Average Case | O(E V^3) |

```cpp
//Adjacency list representation of the graph
class Solution{
    public:
    bool bfs(vector<vector<pair<int, int>>>& rGraph, int src, int dest, vector<int>& parent, int V){
        vector<bool> visited(V, false);
        queue<int> q;
        q.push(src);
        visited[src] = true;
        parent[src] = -1;
        while(!q.empty()){
            int u = q.front();
            q.pop();
            for(auto it : rGraph[u]){
                int v = it.first;
                int wt = it.second;
                if(visited[v] == false && wt > 0){
                    q.push(v);
                    parent[v] = u;
                    visited[v] = true;
                }
            }
        }
        return visited[dest];
    }

    int fordFulkerson(vector<vector<pair<int, int>>>& graph, int src, int dest, int V){
        vector<vector<pair<int, int>>> rGraph = graph;
        vector<int> parent(V);
        int maxFlow = 0;
        while(bfs(rGraph, src, dest, parent, V)){
            int pathFlow = INT_MAX;
            for(int v = dest; v != src; v = parent[v]){
                int u = parent[v];
                for(auto it : rGraph[u]){
                    if(it.first == v){
                        pathFlow = min(pathFlow, it.second);
                        break;
                    }
                }
            }
            for(int v = dest; v != src; v = parent[v]){
                int u = parent[v];
                for(auto& it : rGraph[u]){
                    if(it.first == v){
                        it.second -= pathFlow;
                        break;
                    }
                }
                rGraph[v].push_back({u, pathFlow});
            }
            maxFlow += pathFlow;
        }
        return maxFlow;
    }
}
```

| Time complexity Analysis | Value    |
| ------------------------ | -------- |
| Best Case                | O(V E^2) |
| Worst Case               | O(V E^2) |
| Average Case             | O(V E^2) |

## 10. Construction of a tree from Inorder and Preorder/Postorder Traversal

Given the inorder and preorder/postorder traversal of a binary tree, we can construct the binary tree.

**Algorithm: Using Postorder Traversal**

1. Input: Inorder and postorder traversal of a binary tree.
2. Output: The binary tree.
3. The last element of the postorder traversal is the root of the binary tree.
4. Find the root element in the inorder traversal.
5. The elements to the left of the root element in the inorder traversal are the left subtree of the root.
6. The elements to the right of the root element in the inorder traversal are the right subtree of the root.
7. Recursively construct the left and right subtrees.

```cpp
class Solution{
    public:
    TreeNode* buildTree(vector<int>& inorder, vector<int>& postorder){
        return buildTreePost(inorder, postorder, 0, inorder.size()-1, 0, postorder.size()-1);
    }
    TreeNode* buildTreePost(vector<int>& inorder, vector<int>& postorder, int inStart, int inEnd, int postStart, int postEnd){
        if(inStart > inEnd){
            return nullptr;
        }
        int rootVal = postorder[postEnd];
        TreeNode* root = new TreeNode(rootVal);
        int rootIndex = 0;
        for(int i = inStart; i <= inEnd; i++){
            if(inorder[i] == rootVal){
                rootIndex = i;
                break;
            }
        }
        int leftSize = rootIndex - inStart;
        root->left = buildTreePost(inorder, postorder, inStart, rootIndex-1, postStart, postStart+leftSize-1);
        root->right = buildTreePost(inorder, postorder, rootIndex+1, inEnd, postStart+leftSize, postEnd-1);
        return root;
    }
}
```

```
Example:
Inorder: [9, 3, 15, 20, 7]
Postorder: [9, 15, 7, 20, 3]
Output:
    3
   / \
  9  20
    /  \
   15   7
```

| Time complexity Analysis | Value |
| ------------------------ | ----- |
| Best Case                | O(N)  |
| Worst Case               | O(N)  |
| Average Case             | O(N)  |

## 11. Articulation Points

Aritculation points are those nodes in a graph whose removal increases the number of connected components in the graph.

In other words, represent the vulnerabilities in a connected graph.Single points whose failures would split the network into 2 or more disconnected components.
They are useful in designing reliable networks.

**Algorithm: Naive Approach**

1. Input: A graph with N nodes and E edges.
2. Output: The articulation points in the graph.
3. For each node in the graph, do the following:
   - Remove the node from the graph.
   - Check the number of connected components in the graph.
   - If the number of connected components is greater than the original number of connected components, the node is an articulation point.

```cpp
class Solution{
    public:
    void dfs(int node, vector<vector<int>>& adj, vector<bool>& visited){
        visited[node] = true;
        for(auto it : adj[node]){
            if(!visited[it]){
                dfs(it, adj, visited);
            }
        }
    }
    int findArticulationPoints(vector<vector<int>>& adj, int V){
        int count = 0;
        vector<int>articulationPoints;
        for(int i = 0; i < V; i++){
            vector<bool> visited(V, false);
            visited[i] = true; // marking true before the traversal is effectively removing the node
            int components = 0;
            for(int j = 0; j < V; j++){
                if(!visited[j]){
                    dfs(j, adj, visited);
                    components++;
                }
            }
            if(components > 1){
                count++;
                articulationPoints.push_back(i);
            }
        }
        return count;
    }
}
```

> Here we are using adjacency List representation of the graph.

Here we follow a brute force approach where we remove each node from the graph and check the number of connected components in the graph.
We use DFS to check how many nodes are present in a component.
We run DFS from each node. But before starting the DFS, we mark the node as visited.
This acts like removing the node.
If the `ith` node causes the graph to split then it will cause the `if !visited[j]` condition to be true.
This means that the number of connected components is greater than the original number of connected components.

| Time complexity Analysis | Value     |
| ------------------------ | --------- |
| Best Case                | O(V(V+E)) |
| Worst Case               | O(V(V+E)) |
| Average Case             | O(V(V+E)) |

**Algorithm: Tarjan's Algorithm**:
The idea is to use DFS (Depth First Search). In DFS, follow vertices in a tree form called the DFS tree. In the DFS tree, a vertex `u` is the parent of another vertex `v`, if `v` is discovered by `u`.

In DFS tree, a vertex u is an articulation point if one of the following two conditions is true.

- `u` is the root of the DFS tree and it has at least two children.
- `u` is not the root of the DFS tree and it has a child `v` such that no vertex in the subtree rooted with `v` has a back edge to one of the ancestors in DFS tree of `u`.

1. Input: A graph with N nodes and E edges.
2. Output: The articulation points in the graph.
3. Initialize the discovery time and low time of each node.
4. For each node in the graph, do the following:
   - If the node is not visited, do the following:
     - Find the articulation points using DFS.
5. Return the number of articulation points.

- Discovery time: The time at which the node is discovered in the DFS traversal.
- Low time: The lowest discovery time of the node reachable from the current node.
- Logically Low time tells us what is the minimum discovery time of the node reachable from the current node.

```cpp
class Solution{
    public:
    void dfs(int node, int parent, vector<vector<int>>& adj, vector<int>& disc, vector<int>& low, vector<bool>& visited, vector<bool>& ap, int& time){
        visited[node] = true; // marks the current node as visited
        disc[node] = low[node] = time++; // assigns the discovery time and low time of the node
        int children = 0; // to count the number of children of the node
        for(auto it : adj[node]){ // for each neighbor of the node
            if(!visited[it]){ // if the neighbor is not visited
                children++; // increment the children count ( this node is a child of the current node)
                dfs(it, node, adj, disc, low, visited, ap, time); // recursively call the dfs function
                low[node] = min(low[node], low[it]); // update the low time of the node
                if(parent != -1 && low[it] >= disc[node]){ // if the low time of the neighbor is greater than or equal to the discovery time of the node
                    ap[node] = true; // then its an articulation point
                }
            }else if(it != parent){  // if the neighbor is visited and it is not the parent of the node
                low[node] = min(low[node], disc[it]); // update the low time of the node
            }
        }
        if(parent == -1 && children > 1){ // if the node is the root of the dfs tree and it has more than one child
            ap[node] = true; // we can split the graph by removing the root node
        }
    }
    int findArticulationPoints(vector<vector<int>>& adj, int V){
        vector<int> disc(V, -1);
        vector<int> low(V, -1);
        vector<bool> visited(V, false);
        vector<bool> ap(V, false);
        int time = 0;
        for(int i = 0; i < V; i++){
            if(!visited[i]){
                dfs(i, -1, adj, disc, low, visited, ap, time);
            }
        }
        int count = 0;
        for(int i = 0; i < V; i++){
            if(ap[i]){
                count++;
            }
        }
        return count;
    }
}
```

DFS function:

- Inputs: node, parent-node, adjacency list, discovery time, low time, visited array, articulation points array, and time.
- If the node is not visited, mark the node as visited and assign the discovery time and low time of the node.
- This will tell what time the node got discovered
- Initialize the children count to 0.
- For each neighbor of the node, do the following:
  - If the neighbor is not visited, increment the children count and recursively call the DFS function.
  - Update the low time of the node.
  - If the neighbor is not the parent of the node and the low time of the neighbor is greater than or equal to the discovery time of the node, mark the node as an articulation point.
  - If the neighbor is visited and it is not the parent of the node, update the low time of the node.
- If the node is the root of the DFS tree and it has more than one child, mark the node as an articulation point.

```
Dry run
    0
   / \
  1   2
   \ /
    3
   / \
  4   5

- disc (Discovery time): [-1, -1, -1, -1, -1, -1]
- low (Lowest discovery time reachable): [-1, -1, -1, -1, -1, -1]
- visited (Visited nodes): [false, false, false, false, false, false]
- ap (Articulation points): [false, false, false, false, false, false]
- time: 0
```

| Step | Node | Parent | Children | Disc                    | Low                     | Visited            | AP                 | Time | Comments                          |
| ---- | ---- | ------ | -------- | ----------------------- | ----------------------- | ------------------ | ------------------ | ---- | --------------------------------- |
| 1    | 0    | -1     | 0        | [0, -1, -1, -1, -1, -1] | [0, -1, -1, -1, -1, -1] | [T, F, F, F, F, F] | [F, F, F, F, F, F] | 1    | Root of DFS tree                  |
| 2    | 1    | 0      | 0        | [0, 1, -1, -1, -1, -1]  | [0, 1, -1, -1, -1, -1]  | [T, T, F, F, F, F] | [F, F, F, F, F, F] | 2    | Visit child 1 of 0                |
| 3    | 3    | 1      | 0        | [0, 1, -1, 2, -1, -1]   | [0, 1, -1, 2, -1, -1]   | [T, T, F, T, F, F] | [F, F, F, F, F, F] | 3    | Visit child 3 of 1                |
| 4    | 2    | 3      | 0        | [0, 1, 3, 2, -1, -1]    | [0, 1, 3, 2, -1, -1]    | [T, T, T, T, F, F] | [F, F, F, F, F, F] | 4    | Visit child 2 of 3                |
| 5    | 3    | 2      | 0        | [0, 1, 3, 2, -1, -1]    | [0, 1, 3, 2, -1, -1]    | [T, T, T, T, F, F] | [F, F, F, F, F, F] | 4    | Back to node 3 from 2             |
| 6    | 4    | 3      | 0        | [0, 1, 3, 2, 4, -1]     | [0, 1, 3, 2, 4, -1]     | [T, T, T, T, T, F] | [F, F, F, F, F, F] | 5    | Visit child 4 of 3                |
| 7    | 3    | 4      | 0        | [0, 1, 3, 2, 4, -1]     | [0, 1, 3, 2, 4, -1]     | [T, T, T, T, T, F] | [F, F, F, F, F, F] | 5    | Back to node 3 from 4             |
| 8    | 5    | 3      | 0        | [0, 1, 3, 2, 4, 5]      | [0, 1, 3, 2, 4, 5]      | [T, T, T, T, T, T] | [F, F, F, F, F, F] | 6    | Visit child 5 of 3                |
| 9    | 3    | 5      | 0        | [0, 1, 3, 2, 4, 5]      | [0, 1, 3, 2, 4, 5]      | [T, T, T, T, T, T] | [F, F, F, F, F, F] | 6    | Back to node 3 from 5             |
| 10   | 3    | 1      | 2        | [0, 1, 3, 2, 4, 5]      | [0, 1, 3, 2, 4, 5]      | [T, T, T, T, T, T] | [F, F, F, T, F, F] | 6    | Node 3: Articulation point        |
| 11   | 1    | 0      | 1        | [0, 1, 3, 2, 4, 5]      | [0, 1, 3, 2, 4, 5]      | [T, T, T, T, T, T] | [F, F, F, T, F, F] | 6    | Node 1: Not an articulation point |
| 12   | 0    | -1     | 1        | [0, 1, 3, 2, 4, 5]      | [0, 1, 3, 2, 4, 5]      | [T, T, T, T, T, T] | [F, F, F, T, F, F] | 6    | Node 0: Not an articulation point |

| Time complexity Analysis | Value  |
| ------------------------ | ------ |
| Best Case                | O(V+E) |
| Worst Case               | O(V+E) |
| Average Case             | O(V+E) |

## 12. Bridges

Bridge is a vulnerable edge in a graph. If we remove a bridge, the graph will be disconnected.

**Algorithm: Naive Approach**

1. Input: A graph with N nodes and E edges.
2. Output: The bridges in the graph.
3. For each edge in the graph, do the following:
   - Remove the edge from the graph.
   - Check the number of connected components in the graph.
   - If the number of connected components is greater than the original number of connected components, the edge is a bridge.

```cpp
class Solution{
    public:
    void dfs(int node, vector<vector<int>>& adj, vector<bool>& visited){
        visited[node] = true;
        for(auto it : adj[node]){
            if(!visited[it]){
                dfs(it, adj, visited);
            }
        }
    }
    int findBridges(vector<vector<int>>& adj, int V){
        int count = 0;
        vector<pair<int, int>> bridges;
        for(int i = 0; i < V; i++){
            for(auto it : adj[i]){
                vector<vector<int>> temp = adj;
                temp[i].erase(find(temp[i].begin(), temp[i].end(), it));
                temp[it].erase(find(temp[it].begin(), temp[it].end(), i));
                vector<bool> visited(V, false);
                int components = 0;
                for(int j = 0; j < V; j++){
                    if(!visited[j]){
                        dfs(j, temp, visited);
                        components++;
                    }
                }
                if(components > 1){
                    count++;
                    bridges.push_back({i, it});
                }
            }
        }
        return count;
    }
}
```

| Time complexity Analysis | Value     |
| ------------------------ | --------- |
| Best Case                | O(E(V+E)) |
| Worst Case               | O(E(V+E)) |
| Average Case             | O(E(V+E)) |

**Algorithm: Tarjan's Algorithm**
Here we can use the same algorithm as we used for finding articulation points.

```cpp
class Solution{
    public:
    void dfs(int node, int parent, vector<vector<int>>& adj, vector<int>& disc, vector<int>& low, vector<bool>& visited, vector<pair<int, int>>& bridges, int& time){
        visited[node] = true;
        disc[node] = low[node] = time++;
        for(auto it : adj[node]){
            if(!visited[it]){
                dfs(it, node, adj, disc, low, visited, bridges, time);
                low[node] = min(low[node], low[it]);
                if(low[it] > disc[node]){
                    bridges.push_back({node, it});
                }
            }else if(it != parent){
                low[node] = min(low[node], disc[it]);
            }
        }
    }
    int findBridges(vector<vector<int>>& adj, int V){
        vector<int> disc(V, -1);
        vector<int> low(V, -1);
        vector<bool> visited(V, false);
        vector<pair<int, int>> bridges;
        int time = 0;
        for(int i = 0; i < V; i++){
            if(!visited[i]){
                dfs(i, -1, adj, disc, low, visited, bridges, time);
            }
        }
        return bridges.size();
    }
}
```

The explanation is the same as the one we used for finding articulation points.

| Time complexity Analysis | Value  |
| ------------------------ | ------ |
| Best Case                | O(V+E) |
| Worst Case               | O(V+E) |
| Average Case             | O(V+E) |

## 13. Lowest Common Ancestor (LCA) using Tarjan's Algorithm

LCA in a graph is the lowest common ancestor of two nodes in a graph.
But tarjan's algorithm is used to find strongly connected components in a graph.
We need to modify the algorithm to find the LCA.
We can find the LCA of two nodes in a graph by finding the LCA of the two nodes in the DFS tree.

**Tarjan's Algorithm**:
The idea is to use DFS (Depth First Search). In DFS, follow vertices in a tree form called the DFS tree. In the DFS tree, a vertex `u` is the parent of another vertex `v`, if `v` is discovered by `u`.

In DFS tree, a vertex u is an articulation point if one of the following two conditions is true.

- `u` is the root of the DFS tree and it has at least two children.
- `u` is not the root of the DFS tree and it has a child `v` such that no vertex in the subtree rooted with `v` has a back edge to one of the ancestors in DFS tree of `u`.
- The idea is to find the LCA of two nodes in the DFS tree.
- The LCA of two nodes in the DFS tree is the node with the lowest discovery time in the path from the root to the two nodes.

```cpp
class Solution{
    public:
    void dfs(int node, int parent, vector<vector<int>>& adj, vector<int>& disc, vector<int>& low, vector<bool>& visited, vector<int>& parentArr, int& time){
        visited[node] = true;
        disc[node] = low[node] = time++;
        parentArr[node] = parent;
        for(auto it : adj[node]){
            if(!visited[it]){
                dfs(it, node, adj, disc, low, visited, parentArr, time);
                low[node] = min(low[node], low[it]);
            }else if(it != parent){
                low[node] = min(low[node], disc[it]);
            }
        }
    }
    int findLCA(int u, int v, vector<int>& parentArr, vector<int>& disc, vector<int>& low){
        while(disc[u] > disc[v]){
            u = parentArr[u];
        }
        while(disc[v] > disc[u]){
            v = parentArr[v];
        }
        while(u != v){
            u = parentArr[u];
            v = parentArr[v];
        }
        return u;
    }
    int findLCAinGraph(vector<vector<int>>& adj, int V, int u, int v){
        vector<int> disc(V, -1);
        vector<int> low(V, -1);
        vector<bool> visited(V, false);
        vector<int> parentArr(V, -1);
        int time = 0;
        for(int i = 0; i < V; i++){
            if(!visited[i]){
                dfs(i, -1, adj, disc, low, visited, parentArr, time);
            }
        }
        return findLCA(u, v, parentArr, disc, low);
    }
}
```

In this code, we are finding the LCA of two nodes in a graph using Tarjan's algorithm.

- We are finding the discovery time and low time of each node in the graph.
- We are finding the parent of each node in the graph.
- LCA of two nodes in the graph is the LCA of the two nodes in the DFS tree.
- Hence LCA of two nodes can be either one of the two nodes or the node with the lowest discovery time in the path from the root to the two nodes.

```
Dry run
    0
   / \
  1   2
   \ /
    3
   / \
  4   5

LCA(4, 5) = 3
LCA(4, 3) = 3
LCA(2, 3) = 0
LCA(2, 4) = 0
```

| Time complexity Analysis | Value  |
| ------------------------ | ------ |
| Best Case                | O(V+E) |
| Worst Case               | O(V+E) |
| Average Case             | O(V+E) |

## 14. Bipaertite Matching

A Bipartite graph is a graph whose vertices can be divided into two disjoint sets such that every edge connects a vertex in one set to a vertex in the other set.

Example: A graph is bipartite if it can be colored using two colors such that no two adjacent vertices have the same color.

```
    1 - 2
    |   |
    3 - 4
```

then Set s1 = {1, 3} and Set s2 = {2, 4}.

**Algorithm:**

1. Input: A bipartite graph with N nodes and E edges.
2. Output: The maximum number of matching pairs in the graph.
3. Convert the bipartite graph into a flow network.
4. Find the maximum flow in the flow network.
5. The maximum flow is the maximum number of matching pairs in the graph.

```cpp
class Solution{
    public:
    int maxMatching(vector<vector<int>>& graph, int V){
        vector<vector<int>> flowGraph(V, vector<int>(V, 0)); // Intialize the flow graph flowGraph[u][v] = 0
        for(int i = 0; i < V; i++){
            for(auto it : graph[i]){
                flowGraph[i][it] = 1; // Assign the capacity of the edge from u to v as 1
            }
        }
        int maxFlow = 0; // Initialize the maximum flow as 0
        while(true){ // Repeat the following steps until there is no path from the source node to the sink node, we are performing Ford-Fulkerson algorithm
            vector<int> parent(V, -1); // Initialize the parent array with -1
            queue<int> q; // Initialize a queue
            q.push(0); // Push the source node into the queue
            parent[0] = 0; // Mark the source node as visited
            while(!q.empty()){ // While the queue is not empty
                int u = q.front(); // Get the front element of the queue
                q.pop(); // Pop the front element of the queue
                for(int v = 0; v < V; v++){ // For each neighbor of the node
                    if(parent[v] == -1 && flowGraph[u][v] > 0){ // If the neighbor is not visited and the capacity of the edge is greater than 0
                        parent[v] = u; // Mark the neighbor as visited
                        q.push(v); // Push the neighbor into the queue
                    }
                }
            }
            if(parent[V-1] == -1){ // If the sink node is not visited
                break;
            }
            int pathFlow = INT_MAX; // Initialize the path flow as infinity
            for(int v = V-1; v != 0; v = parent[v]){ // Find the minimum capacity of the path
                int u = parent[v]; // Get the parent of the node
                pathFlow = min(pathFlow, flowGraph[u][v]); // Find the minimum capacity of the path
            }
            for(int v = V-1; v != 0; v = parent[v]){ // Update the flow of the path from sink to source
                int u = parent[v]; // Get the parent of the node
                flowGraph[u][v] -= pathFlow; // Update the flow of the edge from u to v
                flowGraph[v][u] += pathFlow; // Update the flow of the edge from v to u
            }
            maxFlow += pathFlow; // Update the maximum flow
        }
        return maxFlow;
    }
}
```

| Time complexity Analysis | Value    |
| ------------------------ | -------- |
| Best Case                | O(V E^2) |
| Worst Case               | O(V E^2) |
| Average Case             | O(V E^2) |

We can reduce the space complexity by using dfs instead of ford fulkerson algorithm.

```cpp
class Solution{
    public:
    bool dfs(vector<vector<int>>& graph, vector<int>& match, vector<bool>& visited, int u){
        for(auto v : graph[u]){
            if(visited[v]){
                continue;
            }
            visited[v] = true;
            if(match[v] == -1 || dfs(graph, match, visited, match[v])){
                match[v] = u;
                return true;
            }
        }
        return false;
    }
    int maxMatching(vector<vector<int>>& graph, int V){
        vector<int> match(V, -1);
        int count = 0;
        for(int i = 0; i < V; i++){
            vector<bool> visited(V, false);
            if(dfs(graph, match, visited, i)){
                count++;
            }
        }
        return count;
    }
}
```

| Time complexity Analysis | Value |
| ------------------------ | ----- |
| Best Case                | O(VE) |
| Worst Case               | O(VE) |
| Average Case             | O(VE) |

> There is also a Hopcroft-Karp algorithm which is more efficient than the above algorithm.
