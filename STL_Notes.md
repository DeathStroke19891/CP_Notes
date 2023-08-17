
# Table of Contents

1.  [The STL: Introduction](#org362b566)
2.  [STL Headers](#org378d1a5)
3.  [Iterators](#orgbab7f99)
    1.  [Types of Iterators](#org32171d5)
        1.  [Random Access Iterator: vector, deque, array](#org73e9d91)
        2.  [Bidirectional Iterator: list, set/multiset, map/multimap](#org4ea228e)
        3.  [Forward Iterator: forward list](#orgff170a4)
        4.  [Iterators of Unordered Containers](#orgeb7861a)
        5.  [Input Iterator](#org5b48ff3)
        6.  [Output Iterator](#org56296d9)
    2.  [Const Iterators](#orgb4073bf)
    3.  [Iterator functions](#org3443554)
    4.  [Iterator Adaptor](#org2f6795e)
        1.  [Insert Iterator](#org6ae03c4)
        2.  [Iterator Stream](#org28d9d40)
        3.  [Reverse Iterator](#orgc4ce90b)
        4.  [Move Iterator](#orgf215b29)
4.  [Containers](#orgd7d0043)
    1.  [Sequence Containers](#orgc450d43)
        1.  [Vector](#org294b3f7)
        2.  [Deque](#orge8919f3)
        3.  [List](#org4773f43)
        4.  [Forwand List](#org490a580)
        5.  [Array Container](#org0d7ae03)
    2.  [Associative Containers](#orge2c0f7e)
        1.  [Set](#org78f0de2)
        2.  [Multiset](#org98a8031)
        3.  [Map](#orgde46fda)
        4.  [Multimap](#org5904b6d)
    3.  [Unordered Containers](#org5eea0bf)
        1.  [Hash table specific APIs](#org8fc978a)
        2.  [Unordered set](#org663e72e)
        3.  [Unordered multiset](#org4663212)
        4.  [Unordered map](#org00d63b3)
        5.  [Unordered multimap](#orgd9c0b36)
    4.  [Associative arrays](#org95ea690)
    5.  [Container Adaptor](#orgbf9d78e)
        1.  [Stack](#orge41aa6c)
        2.  [Queue](#org2105808)
        3.  [Priority queue](#org4b0b31c)
5.  [Algorithm](#org6463917)
    1.  [Common Vector Algorithms](#org7ad17b5)
        1.  [`sort()`](#org8e3aad7)
        2.  [`min_element()`](#orgb80a756)
        3.  [`reverse()`](#org027db6e)
        4.  [`copy()`](#org182d8ca)
        5.  [`insert()`](#org5353df1)
        6.  [`find_if()`](#orgc4caf78)
6.  [Functors](#orged89d06)



<a id="org362b566"></a>

# The STL: Introduction

The standard template library is a part of the c++ library and its major objective is to provide the implementations of well known algorithms and data structures in the form of templates.

With the help of iterators it is now possible to reduce the number of implementations from n\*m to n+m 
where n is the number of algorithms and m is the number of containers.


<a id="org378d1a5"></a>

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


<a id="orgbab7f99"></a>

# Iterators

This library moves away from object oriented programming by separating the algorithms from the data by introducting a concept called the iterator.
An iterator is a class which has to be implemented by each of the containers(data structures) and the algorithms act on these data structures irrespective of its type.
All iterators behave like pointers and can be dereference to obtain the value.

The iterator abides by the following mathematical notation [begin,end).

ctr.begin() -> first element of the container

ctr.end() -> the one spot after the last element in the container

ctr.cbegin() -> const iterator to first element of the container

ctr.cend() -> const iterator to the one spot after the last element in the container


<a id="org32171d5"></a>

## Types of Iterators


<a id="org73e9d91"></a>

### Random Access Iterator: vector, deque, array

    vector<int> itr;
    itr = itr + 5; // can be added with numbers
    itr = itr - 4;
    if (itr2 > itr1) // can be compared
      ++itr; //faster than itr++
    --itr;


<a id="org4ea228e"></a>

### Bidirectional Iterator: list, set/multiset, map/multimap

    list<int> itr;
    ++itr;
    --itr;


<a id="orgff170a4"></a>

### Forward Iterator: forward list

    forward_list<int> itr;
    ++itr;


<a id="orgeb7861a"></a>

### Iterators of Unordered Containers

They provide at least forward iterators, but have an option to provide bidirectional iterator


<a id="org5b48ff3"></a>

### Input Iterator

Read and process values while iterating forward

    int x = *itr;


<a id="org56296d9"></a>

### Output Iterator

Output values while iterating forward

    *itr = 100;


<a id="orgb4073bf"></a>

## Const Iterators

Provide read only access to container elements.

    for_each(myset.cbegin(), myset.cend(), MyFunction);


<a id="org3443554"></a>

## Iterator functions

    advace(itr, 5);
    distance(itr1, itr2);


<a id="org2f6795e"></a>

## Iterator Adaptor

A special, more powerful iterator


<a id="org6ae03c4"></a>

### Insert Iterator

Used to insert a range of iterators before the insert iterator

    vector<int> vec1 = {4, 5};
    vector<int> vec2 = {12, 14, 16, 18};
    vector<int>::iterator it = find(vec2.begin(), vec2.end(), 16);
    insert_iterator<vector<int> i_itr(vec2, it);
    // insert_iterator<vector<int> i_itr = inserter(vec2, it); // Alternative initialisation
    copy(vec1.begin(), vec1.end(), i_itr);

There are two type of insert iterators:

1.  Back insert iterator
2.  Front insert iterator


<a id="org28d9d40"></a>

### Iterator Stream

    vector<string> vec4;
    copy(istream_iterator<string>(cin), back_inserter(vec4));
    
    copy(vec4.begin(), vec4.end(), ostream_iterator<string>(cout, " "));
    
    // Complicated example
    
    copy(istream_iterator<string>(cin), istream_iterator<string>(), ostream_iterator<string>(cout, " "));


<a id="orgc4ce90b"></a>

### Reverse Iterator

Reverse iterator can traverse a container in reverse order.

    vector<int> vec = {4, 5, 6, 7};
    reverse_iterator<vector<int>::iterator> ritr;
    for(ritr = vec.rbegin(); ritr != vec.rend(); ritr++){
      cout << *ritr << endl;
    }


<a id="orgf215b29"></a>

### Move Iterator


<a id="orgd7d0043"></a>

# Containers


<a id="orgc450d43"></a>

## Sequence Containers

Typically implemented with arrays or linked lists. The sequence containers include:

1.  Array *stl*
2.  Linked List
3.  vector *stl*
4.  deque *stl*
5.  list *stl*
6.  forward list *stl*


<a id="org294b3f7"></a>

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


<a id="orge8919f3"></a>

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


<a id="org4773f43"></a>

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


<a id="org490a580"></a>

### Forwand List

Same as list but only forward pointers


<a id="org0d7ae03"></a>

### Array Container

    array<int, 3> a = {3, 4, 5};
    a.begin();
    a.end();
    a.size();
    a.swap();
    
    // Size cannot change
    
    array<int, 4> b = {3, 4, 5};
    // Here a and b are of different types due to their different sizes


<a id="orge2c0f7e"></a>

## Associative Containers

Typically implemented with a binary tree. The key feature of these containers is the fact that all the elements are always sorted.
These include

1.  set, multiset *stl*
2.  map, multimap *stl*

By default as elements are sorted by < and any operation insertion or removal maintains the sorted order.

Associative actually comes from the map where a value is associated with the key.
The set and multiset can be thought of as a special case where the key == value.


<a id="org78f0de2"></a>

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


<a id="org98a8031"></a>

### Multiset

Multiset is a set that allows duplicate items. Value of the element cannot be modified.

1.  Properties of a MultiSet

    1.  Fast search: O(log(n))
    2.  Traversing is slow (compared to vector & deque)
    3.  No random access, no [] operator.


<a id="orgde46fda"></a>

### Map

Map doesn't allow elements with duplicate keys. The map is sorted according to the value of the key.
The key of a map cannot be modified.

1.  Properties of a Map

    1.  Insertion takes O(log(n))
    2.  Search/Find takes O(log(n))
    3.  With hints, insertion takes O(1)
    4.  Traversing is slow (compared to vector & deque)

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


<a id="org5904b6d"></a>

### Multimap

Multimap is a map that allows duplicated keys. The key of a map cannot be modified.
No random access, no [] operator.


<a id="org5eea0bf"></a>

## Unordered Containers

Typically implemented with a hash table.
These include

1.  unordered set/multiset *stl*
2.  unordered map/multimap *stl*


<a id="org8fc978a"></a>

### Hash table specific APIs

    myset.load_factor(); // ratio of total no of elements and total no of buckets
    myset.bucket(x);
    myset.bucket_count();


<a id="org663e72e"></a>

### Unordered set

Unordered set has no duplicate elements. Value of the key cannot be modified.

    vector<string> vec = {"purple", "pink"};
    myset.insert(vec.begin(), vec.end());

There is no random access, no [] operator.


<a id="org4663212"></a>

### Unordered multiset

Unordered set with duplicated elements. Maintains a count for each element.
Takes more space compared to unordered set.
No random access, no [] operator.


<a id="org00d63b3"></a>

### Unordered map

Unordered set of pairs. 


<a id="orgd9c0b36"></a>

### Unordered multimap

Unordered map that allows duplicated keys. Uses chaining or some sort of probing mechanism.
No random acesss, no [] operator. 


<a id="org95ea690"></a>

## Associative arrays

1.  Properties of Assciative array

    1.  Seach time: unordered map: O(1); map: O(log(n))
    2.  Unordered\_ map may degrade to O(n)
    3.  Can't use multimap and unordered multimap as they don't have [] operator.


<a id="orgbf9d78e"></a>

## Container Adaptor

Provide a restricted interface to meet special needs.
Implemented with fundamental container classes


<a id="orge41aa6c"></a>

### Stack

LIFO, push(), pop(), top()


<a id="org2105808"></a>

### Queue

FIFO, push(), pop(), front(), back()


<a id="org4b0b31c"></a>

### Priority queue

push(), pop(), top()


<a id="org6463917"></a>

# Algorithm

There are some common APIs provided by all containers

1.  .empty()
2.  .size()
3.  copy constructor
    
        vector<int> vec2(vec); // Copy constructor
4.  .clear()
5.  .swap()


<a id="org7ad17b5"></a>

## Common Vector Algorithms

These algorithms are not limited to vectors but are most commonly used with them.


<a id="org8e3aad7"></a>

### `sort()`

This algorithm takes two iterators and sorts all the elements in the range between the two iterators.


<a id="orgb80a756"></a>

### `min_element()`

returns the minimum element in the range between the iterators given in the arguments.


<a id="org027db6e"></a>

### `reverse()`

Reverses the elements between the given range


<a id="org182d8ca"></a>

### `copy()`

Copy from source to destination

    vector<int> vec2(3);
    copy(itr, vec.end(), // Source
         vec2.begin()); // Destination


<a id="org5353df1"></a>

### `insert()`

    vec3.insert(vec3.end(), itr, vec.end());


<a id="orgc4caf78"></a>

### `find_if()`

    vector<int>::iterator itr = find_if(vec.begin(), vec.end(), isOdd); // where isOdd is a function


<a id="orged89d06"></a>

# Functors

