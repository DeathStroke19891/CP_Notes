# Table of Contents

| Sl. No. | Topic                                                   |
| ------- | ------------------------------------------------------- |
| 1       | [Introduction to Graphs](#1-introduction-to-graphs)     |
| 2       | [Representation of Graphs](#2-representation-of-graphs) |
| 3       | [Graph Traversal](#3-graph-traversal)                   |

---

# 1. Introduction to Graphs

A Graph is a non-linear data structure consisting of nodes and edges. The nodes are sometimes also referred to as vertices and the edges are lines or arcs that connect any two nodes in the graph.

> A Graph consists of a finite set of vertices(or nodes) and set of Edges which connect a pair of nodes.

# 2. Representation of Graphs

Graphs can be represented in multiple ways. The two most common ways are:

1. Adjacency Matrix
2. Adjacency List

## Adjacency Matrix

In adjacency matrix, the nodes of graph are represented as rows and columns of a matrix.
If there are `n` nodes in a graph, then the adjacency matrix will be of size `n x n`.

- If there is a node from Node A to Node B, then the value at `matrix[A][B]` will be 1.
- If there is no edge between Node A and Node B, then the value at `matrix[A][B]` will be 0.

Lets say the graph is as follows:

```
    0
   / \
  1---3
   \ /
    2
```

```cpp
// Adjacency Matrix
int adj[4][4] = {
    {0, 1, 1, 0},
    {1, 0, 1, 1},
    {1, 1, 0, 1},
    {0, 1, 1, 0}
};
```

## Adjacency List

In adjacency list, the graph is represented as an array of linked lists. The size of the array is equal to the number of nodes in the graph.

If we assume there are `n` nodes in the graph, then the adjacency list will be of size `n`.

- adj[i] will contain all the nodes that are connected to node `i`.

Lets say the graph is as follows:

```
    0
   / \
  1---3
   \ /
    2
```

```cpp
vector<int> adj[4];
adj[0].push_back(1);
adj[0].push_back(3);
adj[1].push_back(0);
adj[1].push_back(2);
adj[1].push_back(3);
adj[2].push_back(1);
adj[2].push_back(3);
adj[3].push_back(0);
adj[3].push_back(1);
adj[3].push_back(2);

// Represntation of Adjacency List
// 0 = 1->3->NULL
// 1 = 0->2->3->NULL
// 2 = 1->3->NULL
// 3 = 0->1->2->NULL
```

# 3. Graph Traversal

## 1. Breadth First Search (BFS)

- The traversal is similar to trees but here it **may contain cycles**.

So to overcome this problem we need to maintain a visited array to keep track of the nodes that are visited.

**BFS Algorithm:**
Input: Graph G, Source Node S
Output: Traversal of Graph G from Source Node S

1. Create a `queue` and a `visited` boolean array.
2. While the queue is not empty, do the following:
   - Pop the front element of the queue and print it.
   - Traverse all the adjacent nodes of the popped element and if they are not visited, mark them as visited and push them into the queue.

- `int V` : Number of vertices in the graph.
- `vector<int> adj[]` : Adjacency List.
- `int S` : Source Node.

```cpp
void bfs(vector<int> adj[], int V, int S) {
    queue<int> q;
    vector<bool> visited(V, false);

    q.push(S);
    visited[S] = true;

    while (!q.empty()) {
        int node = q.front();
        cout << node << " ";
        q.pop();

        for (int i = 0; i < adj[node].size(); i++) {
            if (!visited[adj[node][i]]) {
                q.push(adj[node][i]);
                visited[adj[node][i]] = true;
            }
        }
    }
}
```

### Time Complexity

- If we use an adjacency list to represent the graph, then the time complexity of BFS is `O(V + E)`, where `V` is the number of vertices and `E` is the number of edges in the graph.
- Space Complexity is `O(V)`.
- If we use an adjacency matrix to represent the graph, then the time complexity of BFS is `O(V^2)`.
- Space Complexity is `O(V)`.

### Applications of BFS

1. Shortest Path in Unweighted Graphs.
2. Peer to Peer Networks.
3. Crawlers in Search Engines.

## 2. Depth First Search (DFS)

- The traversal is similar to trees but here it **may contain cycles**.
- To prevent this we will use a boolean array to keep track of visited nodes.

**DFS Algorithm:**
Input: Graph G, Source Node S
Output: Traversal of Graph G from Source Node S

1. Create a `stack` and a `visited` boolean array.
2. Push the source node into the stack and mark it as visited.
3. While the stack is not empty, do the following:
   - Pop the top element of the stack and print it.
   - Traverse all the adjacent nodes of the popped element and if they are not visited, mark them as visited and push them into the stack.

- `int V` : Number of vertices in the graph.
- `vector<int> adj[]` : Adjacency List.
- `int S` : Source Node.

```cpp
void dfs(vector<int> adj[], int V, int S) {
    stack<int> st;
    vector<bool> visited(V, false);

    st.push(S);
    visited[S] = true;

    while (!st.empty()) {
        int node = st.top();
        cout << node << " ";
        st.pop();

        for (int i = 0; i < adj[node].size(); i++) {
            if (!visited[adj[node][i]]) {
                st.push(adj[node][i]);
                visited[adj[node][i]] = true;
            }
        }
    }
}
```

### Time Complexity

- If we use an adjacency list to represent the graph, then the time complexity of DFS is `O(V + E)`, where `V` is the number of vertices and `E` is the number of edges in the graph.
- Space Complexity is `O(V)`.
- If we use an adjacency matrix to represent the graph, then the time complexity of DFS is `O(V^2)`.
- Space Complexity is `O(V)`.

### Applications of DFS

1. Topological Sorting.
2. Solving Puzzles with only one solution.
3. Path Finding.
4. Detecting Cycles in a Graph.
