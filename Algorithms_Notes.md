# Table of Contents

| Sl. No. | Topic |
| ------- | ----- |
| 1       |       |
| 2       |       |
| 3       |       |

---

# Subtopics

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
