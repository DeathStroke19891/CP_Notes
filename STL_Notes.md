
# Table of Contents

1.  [The STL: Introduction](#orgd366517)
2.  [STL Headers](#org831251e)
3.  [Iterators](#orga814ddf)
    1.  [Types of Iterators](#org3a65c92)
        1.  [Random Access Iterator: vector, deque, array](#org56b7380)
        2.  [Bidirectional Iterator: list, set/multiset, map/multimap](#org19ae0f8)
        3.  [Forward Iterator: forward list](#orgf9c2753)
        4.  [Iterators of Unordered Containers](#orge7f445a)
        5.  [Input Iterator](#orgc0f183a)
        6.  [Output Iterator](#org8208ca8)
    2.  [Const Iterators](#orgfb40774)
    3.  [Iterator functions](#org9fc7c38)
    4.  [Iterator Adaptor](#orga1aee7b)
        1.  [Insert Iterator](#orgc0b94d0)
        2.  [Stream Iterator](#org0549702)
        3.  [Reverse Iterator](#org26bd28e)
        4.  [Move Iterator](#org7c24ebb)
4.  [Containers](#org2a0fd29)
    1.  [Sequence Containers](#org4b3c364)
        1.  [Vector](#org88dcc8c)
        2.  [Deque](#orge645d2a)
        3.  [List](#org0eaf75e)
        4.  [Forwand List](#org293ba77)
        5.  [Array Container](#org36e193c)
    2.  [Associative Containers](#orgc0c5d0a)
        1.  [Set](#orgd0b7363)
        2.  [Multiset](#org62518f1)
        3.  [Map](#org463d1f3)
        4.  [Multimap](#orgcdfb953)
    3.  [Unordered Containers](#orgb0ed5e2)
        1.  [Hash table specific APIs](#org0ba938f)
        2.  [Unordered set](#org83139ae)
        3.  [Unordered multiset](#orgbef8ad8)
        4.  [Unordered map](#orgde4d982)
        5.  [Unordered multimap](#org435f962)
    4.  [Associative arrays](#org899a051)
    5.  [Container Adaptor](#org3f4406c)
        1.  [Stack](#orgd0bce67)
        2.  [Queue](#orgfe52ae5)
        3.  [Priority queue](#org9e1fc78)
5.  [Algorithm](#org272040e)
    1.  [sort()](#org842fde1)
6.  [Functors](#org72e161e)



<a id="orgd366517"></a>

# The STL: Introduction

The standard template library is a part of the c++ library and its major objective is to provide the implementations of well known algorithms and data structures in the form of templates.

With the help of iterators it is now possible to reduce the number of implementations from n\*m to n+m 
where n is the number of algorithms and m is the number of containers.


<a id="org831251e"></a>

# STL Headers

    #include <vector>
    #include <deque>
    #include <list>
    #include <set> // set and multiset
    #include <map> // map and multimap
    #include <unordered_set> // unordered set/multiset
    #include <unordered_map> // unordered map/multimap
    #include <iterator>
    #include <algorithm>
    #include <numeric> // some numeric algorithms
    #include <functional>


<a id="orga814ddf"></a>

# Iterators

This library moves away from object oriented programming by separating the algorithms from the data by introducting a concept called the iterator.
An iterator is a class which has to be implemented by each of the containers(data structures) and the algorithms act on these data structures irrespective of its type.
All iterators behave like pointers and can be dereference to obtain the value.

The iterator abides by the following mathematical notation [begin,end).

ctr.begin() -> first element of the container

ctr.end() -> the one spot after the last element in the container

ctr.cbegin() -> const iterator to first element of the container

ctr.cend() -> const iterator to the one spot after the last element in the container


<a id="org3a65c92"></a>

## Types of Iterators


<a id="org56b7380"></a>

### Random Access Iterator: vector, deque, array

    vector<int> itr;
    itr = itr + 5; // can be added with numbers
    itr = itr - 4;
    if (itr2 > itr1) // can be compared
      ++itr; //faster than itr++
    --itr;


<a id="org19ae0f8"></a>

### Bidirectional Iterator: list, set/multiset, map/multimap

    list<int> itr;
    ++itr;
    --itr;


<a id="orgf9c2753"></a>

### Forward Iterator: forward list

    forward_list<int> itr;
    ++itr;


<a id="orge7f445a"></a>

### Iterators of Unordered Containers

They provide at least forward iterators, but have an option to provide bidirectional iterator


<a id="orgc0f183a"></a>

### Input Iterator

Read and process values while iterating forward

    int x = *itr;


<a id="org8208ca8"></a>

### Output Iterator

Output values while iterating forward

    *itr = 100;


<a id="orgfb40774"></a>

## Const Iterators

Provide read only access to container elements.

    for_each(myset.cbegin(), myset.cend(), MyFunction);


<a id="org9fc7c38"></a>

## Iterator functions

    advace(itr, 5);
    distance(itr1, itr2);


<a id="orga1aee7b"></a>

## Iterator Adaptor

A special, more powerful iterator


<a id="orgc0b94d0"></a>

### Insert Iterator

    vector<int> vec1 = {4, 5};
    vector<int> vec2 = {12, 14, 16, 18};
    vector<int>::iterator it = find(vec2.begin(), vec2.end(), 16);
    insert_iterator<vector<int> i_itr(vec2, it);
    copy(vec1.begin(), vec1.end(), i_itr);


<a id="org0549702"></a>

### Stream Iterator


<a id="org26bd28e"></a>

### Reverse Iterator


<a id="org7c24ebb"></a>

### Move Iterator


<a id="org2a0fd29"></a>

# Containers


<a id="org4b3c364"></a>

## Sequence Containers

Typically implemented with arrays or linked lists. The sequence containers include:

1.  Array *stl*
2.  Linked List
3.  vector *stl*
4.  deque *stl*
5.  list *stl*
6.  forward list *stl*


<a id="org88dcc8c"></a>

### Vector

1.  Properties of a vector

    1.  Fast insert/remove at the end: O(1)
    2.  Slow insert/remove at the beginning or in the middle: O(n)
    3.  slow search: O(n)

2.  Important Features and titbits for CP

        for(auto it: vec) // This is faster than the normal looping over the vector elements like an array
          cout << it << " ";
        
        // Vectors are dynamically allocated contiguous array in memory
        int* p = &vec[0];
        p[2] = 6; // This works!!


<a id="orge645d2a"></a>

### Deque

Deque and vector has very similar interfaces.
The only difference is that the vector can only grow in the end, while a deque can grow on both sides.
However the underlying implementation of deque does not provide contiguous memory allocation

1.  Properties of a deque

    1.  Fast insert/remove at the beginning and the end: O(1)
    2.  slow insert/remove in the middle: O(n)
    3.  slow search: O(n)

2.  Important Features and titbits for CP

        deque<int> deq = { 4, 6, 7};
        deq.push_front(2);
        deq.push_back(3);
        
        // Deque has similar interface with vector
        cout << deq[1];


<a id="org0eaf75e"></a>

### List

A list is a doubly linked list.

1.  Properties of a List

    1.  Fast insert/remove at any place: O(1)
    2.  No random access, no [] operator
    3.  slow search: O(n), slower than vector because of cache
    4.  But it has a killer function, which is splice

2.  Important Features and titbits for CP

        list<int>::iterator itr = find(mylist.begin(), mylist.end(), 2);
        mylist.insert(itr, 8) // inserts 8 in front of the itr
        itr++;
        mylist.erase(itr) // removal with O(1)
        
        // Splice
        mylist1.splice(itr, mylist2, itr_a, itr_b); // O(1)
                                  // Takes all the data(nodes) between itr_a, itr_b
                      // stores it in mylist1 at itr and this takes constant time


<a id="org293ba77"></a>

### Forwand List

Same as list but only forward pointers


<a id="org36e193c"></a>

### Array Container

    array<int, 3> a = {3, 4, 5};
    a.begin();
    a.end();
    a.size();
    a.swap();
    
    // Size cannot change
    
    array<int, 4> b = {3, 4, 5};
    // Here a and b are of different types due to their different sizes


<a id="orgc0c5d0a"></a>

## Associative Containers

Typically implemented with a binary tree. The key feature of these containers is the fact that all the elements are always sorted.
These include

1.  set, multiset *stl*
2.  map, multimap *stl*

By default as elements are sorted by < and any operation insertion or removal maintains the sorted order.

Associative actually comes from the map where a value is associated with the key.
The set and multiset can be thought of as a special case where the key == value.


<a id="orgd0b7363"></a>

### Set

Set has no duplicate items. Value of the elements cannot be modified

1.  Properties of a Set

    1.  Insertion takes O(log(n))
    2.  Search/Find takes O(log(n))
    3.  With hints, insertion takes O(1)
    4.  Traversing is slow (compared to vector & deque)
    5.  No random access, no [] operator.

2.  Important Features and titbits for CP

        set<int> myset;
        myset.insert(3);
        myset.insert(1);
        myset.insert(7);
        
        set<int>::iterator it;
        it = myset.find(7);
        
        pair<set<int>::iterator, bool> ret;
        ret = myset.insert(3);
        if(ret.second == false)
          it=ret.first;
        
        myset.insert(it, 9); //This reduces insertion to O(1)
        myset.erase(it);


<a id="org62518f1"></a>

### Multiset

Multiset is a set that allows duplicate items. Value of the element cannot be modified.

1.  Properties of a MultiSet

    1.  Fast search: O(log(n))
    2.  Traversing is slow (compared to vector & deque)
    3.  No random access, no [] operator.


<a id="org463d1f3"></a>

### Map

Map doesn't allow elements with duplicate keys. The map is sorted according to the value of the key.
The key of a map cannot be modified.

1.  Properties of a Map

    1.  

2.  Important Features and titbits for CP

        map<char, int> mymap;
        mymap.insert ( pair<char, int>('a', 100));
        mymap.insert ( make_pair('z', 200));
        
        map<char, int>::iterator it = mymap.begin();
        mymap.insert(it, pair<char, int>('b', 300));
        
        it = mymap.find('z'); // O(log(n))
        
        for( it=mymap.begin(); it != mymap.end(); it++){
          cout << (*it).first << " => " << (*it).second << endl;
        }


<a id="orgcdfb953"></a>

### Multimap

Multimap is a map that allows duplicated keys. The key of a map cannot be modified.
No random access, no [] operator.


<a id="orgb0ed5e2"></a>

## Unordered Containers

Typically implemented with a hash table.
These include

1.  unordered set/multiset *stl*
2.  unordered map/multimap *stl*


<a id="org0ba938f"></a>

### Hash table specific APIs

    myset.load_factor(); // ratio of total no of elements and total no of buckets
    myset.bucket(x);
    myset.bucket_count();


<a id="org83139ae"></a>

### Unordered set

Unordered set has no duplicate elements. Value of the key cannot be modified.

    vector<string> vec = {"purple", "pink"};
    myset.insert(vec.begin(), vec.end());

There is no random access, no [] operator.


<a id="orgbef8ad8"></a>

### Unordered multiset

Unordered set with duplicated elements. Maintains a count for each element.
Takes more space compared to unordered set.
No random access, no [] operator.


<a id="orgde4d982"></a>

### Unordered map

Unordered set of pairs. 


<a id="org435f962"></a>

### Unordered multimap

Unordered map that allows duplicated keys. Uses chaining or some sort of probing mechanism.
No random acesss, no [] operator. 


<a id="org899a051"></a>

## Associative arrays

1.  Properties of Assciative array

    1.  Seach time: unordered map: O(1); map: O(log(n))
    2.  Unordered\_ map may degrade to O(n)
    3.  Can't use multimap and unordered multimap as they don't have [] operator.


<a id="org3f4406c"></a>

## Container Adaptor

Provide a restricted interface to meet special needs.
Implemented with fundamental container classes


<a id="orgd0bce67"></a>

### Stack

LIFO, push(), pop(), top()


<a id="orgfe52ae5"></a>

### Queue

FIFO, push(), pop(), front(), back()


<a id="org9e1fc78"></a>

### Priority queue

push(), pop(), top()


<a id="org272040e"></a>

# Algorithm

There are some common APIs provided by all containers

1.  .empty()
2.  .size()
3.  copy constructor
    
        vector<int> vec2(vec); // Copy constructor
4.  .clear()
5.  .swap()


<a id="org842fde1"></a>

## sort()

This algorithm takes two iterators and sorts all the elements in the range between the two iterators.


<a id="org72e161e"></a>

# Functors

