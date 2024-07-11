# Table of Contents

| Sl. No. | Topic                                                   |
|---------|---------------------------------------------------------|
| 1       | [Introduction to Graphs](#1-introduction-to-graphs)     |
| 2       | [Representation of Graphs](#2-representation-of-graphs) |
| 3       | [Graph Traversal](#3-graph-traversal)                   |
| 4       | [Bipartite Graphs](#4-bipartite-graphs)                 |
| 5       | [Disjoint Sets](#5-disjoint-sets)                       |

---

## Subtopics under graph traversal

| Sl. No. | Subtopic                                                                                                                        |
| ------- | ------------------------------------------------------------------------------------------------------------------------------- |
| 3.1     | [Breadth First Search (BFS)](#1-breadth-first-search-bfs)                                                                       |
| 3.2     | [Depth First Search (DFS)](#2-depth-first-search-dfs)                                                                           |
| 3.3     | [Finding All Ancestors in a Directed Acyclic Graph (DAG)](#3-finding-all-ancestors-in-a-directed-acyclic-graph-dag)             |
| 3.4     | [Detecting a cycle in a Directed Graph](#4-detecting-a-cycle-in-a-directed-graph)                                               |
| 3.5     | [Detecting a cycle in a Directed Graph using Topological Sort](#5-detecting-a-cycle-in-a-directed-graph-using-topological-sort) |
| 3.6     | [Detecting a cycle in an Undirected Graph using DFS](#6-detecting-a-cycle-in-an-undirected-graph-using-dfs)                     |
| 3.7     | [Longest path in a Weighted Directed Acyclic Graph (DAG)](#7-longest-path-in-a-weighted-directed-acyclic-graph-dag)             |
| 3.8     | [Topological Sort](#8-topological-sort)                                                                                         |

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

## 3. Finding All Ancestors in a Directed Acyclic Graph (DAG)

- [Problem Link](https://leetcode.com/problems/all-ancestors-of-a-node-in-a-directed-acyclic-graph/description)

- [Solution](https://kts-o7.github.io/blog/posts/problem-all-ancestors-of-a-node-in-a-dag/)
- When given a positive integer `n` and `vector<vector<int>> edges` representing a directed acyclic graph, return a list of all the ancestors of all the nodes in the graph. The list must be sorted in ascending order.

```cpp
class Solution {
public:
void dfs(vector<bool>& visited, vector<vector<int>>& adjList, vector<vector<int>>& ancestor ,int parent, int curr)
{
        visited[curr] = true;
        for( int forward:adjList[curr])
        {
            if(!visited[forward])
            {
                ancestor[forward].push_back(parent);
                dfs(visited,adjList,ancestor,parent,forward);
            }
        }
    }

    vector<vector<int>> getAncestors(int n, vector<vector<int>>& edges) {
        std::ios::sync_with_stdio(false);
        cin.tie(nullptr);
        cout.tie(nullptr);
        vector<vector<int>> adjList(n);
        vector<vector<int>> ancestor(n);

        for (const auto& edge : edges) {
            adjList[edge[0]].push_back(edge[1]);
        }


        for(int i = 0; i<n; i++){
            vector<bool>visited(n,false);
            dfs(visited,adjList,ancestor,i,i);
        }

        // No need to sort again as the answer itself is sorted.
        //for(int i = 0;i <n; i++)
            //sort(ancestor[i].begin(),ancestor[i].end());

        return ancestor;

    }
};
```

Here we use DFS traversal to build the ancestor list for each of the nodes in the graph.
We use `Adjacency List` to store the graph and `ancestor` to store the ancestors of each node.

**Algorithm**:

1. Create an adjacency list to store the graph.
2. Create a vector of vectors `ancestor` to store the ancestors of each node.
3. For each node in the graph, do the following:
- Create a visited array and call the DFS function.
- In the DFS function, mark the current node as visited and for each adjacent node, if it is not visited, mark it as visited and push the parent node into the ancestor list.
4. Return the ancestor list.

**Algorithm for DFS**:
Input: Graph in form of adjacency list, visited array, ancestor array, parent node, current node
Output: Ancestor list for each node

1. First mark the current node as visited.
2. For each adjacent node of the current node, do the following:
- If the adjacent node is not visited, mark it as visited and push the parent node into the ancestor list of the adjacent node.
- Call the DFS function recursively for the adjacent node.

**Time Complexity**:

- The time complexity of the above solution is `O(V + E)`, where `V` is the number of vertices and `E` is the number of edges in the graph.
- This is because we call the DFS function for each node in the graph.
- And each node may be connected to at most `V-1` other nodes.

**Space Complexity**:

- The space complexity of the above solution is `O(V + E)`.
- This is because we use an adjacency list to store the graph and a vector of vectors to store the ancestors of each node.

## 4. Detecting a cycle in a Directed Graph

- To find a cycle in a directed graph, we can use the DFS traversal.
- It is based on the fact that a graph has a cycle if and only if there is a back edge in the graph.
- To detect a back edge, we need to keep track if the nodes visited till now and if we encounter a node that is already visited and is not the parent of the current node, then there is a cycle in the graph.

**Algorithm**:

- Create a recursive dfs function that takes the current node, parent node, visited array, and recursion stack as arguments.
- Mark the current node as visited and push it into the recursion stack.
- For each adjacent node of the current node, do the following:
- If the adjacent node is not visited, call the dfs function recursively for the adjacent node.
- If the adjacent node is visited and is not the parent of the current node, then there is a cycle in the graph.
- If there is a cycle, return true.
- After the loop, pop the current node from the recursion stack.
- Return false.

```cpp
class Solution {
public:
    bool dfs(vector<vector<int>>& adj, vector<bool>& visited, vector<bool>& recStack, int curr) {
        visited[curr] = true;
        recStack[curr] = true;

        for (int i = 0; i < adj[curr].size(); i++) {
            int next = adj[curr][i];
            if (!visited[next]) {
                if (dfs(adj, visited, recStack, next)) {
                    return true;
                }
            } else if (recStack[next]) {
                return true;
            }
        }

        recStack[curr] = false;
        return false;
    }

    bool hasCycle(int V, vector<vector<int>>& edges) {
        vector<vector<int>> adj(V);
        for (int i = 0; i < edges.size(); i++) {
            adj[edges[i][0]].push_back(edges[i][1]);
        }

        vector<bool> visited(V, false);
        vector<bool> recStack(V, false);

        for (int i = 0; i < V; i++) {
            if (!visited[i]) {
                if (dfs(adj, visited, recStack, i)) {
                    return true;
                }
            }
        }

        return false;
    }
};
```

Why do we keep a recursive stack ?
We use recursive stack to keep track of the nodes that are currently in the recursion stack.
Recursion stack represents the nodes that are already reached in the current traversal.
If we encounter a node that is already in the recursion stack, then there is a cycle in the graph.

## 5. Detecting a cycle in a Directed Graph using Topological Sort

- Topological sort is the linear ordering of vertices such that for every directed edge `u -> v`, vertex `u` comes before `v` in the ordering.
- If a graph has a cycle, then it cannot have a topological sort.
- So, to detect a cycle in a directed graph, we can use the topological sort algorithm.

**Algorithm**:

1. Input: Graph G, Number of vertices V, Edges E
2. Output: True if the graph has a cycle, False otherwise
- Create an adjacency list to store the graph.
- Create an indegree array to store the indegree of each node.
- Create a queue to store the nodes with indegree 0.
- Initialize the indegree array and the queue.
- While the queue is not empty, do the following:
- Pop the front element of the queue and increment the count of visited nodes.
- Traverse all the adjacent nodes of the popped element and decrement their indegree.
- If the indegree of any adjacent node becomes 0, push it into the queue.
- If the count of visited nodes is not equal to the number of vertices, return true.
- Otherwise, return false.

```cpp
class Solution {
public:
    bool hasCycle(int V, vector<vector<int>>& edges) {
    // V is the number of vertices in the graph
        vector<vector<int>> adj(V);
    // Indegree means number of incoming edges to a node
        vector<int> indegree(V, 0);

        for (int i = 0; i < edges.size(); i++) {
            adj[edges[i][0]].push_back(edges[i][1]);
            indegree[edges[i][1]]++;
        }

        queue<int> q;
        int count = 0;

        for (int i = 0; i < V; i++) {
            if (indegree[i] == 0) {
                q.push(i);
            }
        }

        while (!q.empty()) {
            int node = q.front();
            q.pop();
            count++;

            for (int i = 0; i < adj[node].size(); i++) {
                indegree[adj[node][i]]--;
                if (indegree[adj[node][i]] == 0) {
                    q.push(adj[node][i]);
                }
            }
        }

        return count != V;
    }
};
```

Here we are visiting each node once and each edge once.
if Indegrees of every node is greater than 0 it means there is already a cycle in the graph.
if not then we will check if the count of visited nodes is equal to the number of vertices or not.
if the count is less than the number of vertices then there is a cycle in the graph.

## 6. Detecting a cycle in an Undirected Graph using DFS

We can say a cycle is present in an undirected graph if there is a back edge in the graph.
To find the back egde of any of the node's ancestors we can check by a visited array.

**Algorithm**:

- Iterate over all the nodes in the graph and keep a boolean array `visited` to keep track of the visited nodes.
- For each node, if it is not visited, call the DFS function.
- In the DFS function, mark the current node as visited and for each adjacent node, if it is not visited, call the DFS function recursively.
- If the adjacent node is visited and is not the parent of the current node, then there is a cycle in the graph.

```cpp
class Solution {
public:
    bool dfs(vector<vector<int>>& adj, vector<bool>& visited, int parent, int curr) {
        visited[curr] = true;

        for (int i = 0; i < adj[curr].size(); i++) {
            int next = adj[curr][i];
            if (!visited[next]) {
                if (dfs(adj, visited, curr, next)) {
                    return true;
                }
            } else if (next != parent) {
                return true;
            }
        }
        return false;
    }

    bool hasCycle(int V, vector<vector<int>>& edges) {
        vector<vector<int>> adj(V);
        for (int i = 0; i < edges.size(); i++) {
            adj[edges[i][0]].push_back(edges[i][1]);
            adj[edges[i][1]].push_back(edges[i][0]);
        }

        vector<bool> visited(V, false);

        for (int i = 0; i < V; i++) {
            if (!visited[i]) {
                if (dfs(adj, visited, -1, i)) {
                    return true;
                }
            }
        }
        return false;
    }
};
```

The above code first calls the `dfs` function for each node in the graph.
In the `dfs` function, we mark the current node as visited and for each adjacent node, if it is not visited, call the `dfs` function recursively.
If the adjacent node is visited and is not the parent of the current node, then there is a cycle in the graph.
If the `dfs` function completes without finding a cycle, then return false.

- Here base case is when the adjacent node is visited and is not the parent of the current node, then there is a cycle in the graph.

## 7. Longest path in a Weighted Directed Acyclic Graph (DAG)

- Given a Weighted Directed Acyclic Graph (DAG) and a source vertex `s` in it, find the longest distances from `s` to all other vertices in the given graph.

> The longest path problem for a graph is a NP-Hard problem.

However for DAG, we can find the longest path in `O(V+E)` time using topological sorting.

**Algorithm**:

1. First initialize the distance array with negative infinity and distance of source vertex as 0.
2. Then do a topological sort of the graph.
3. Once we obtain topological order, we can iterate over all the vertices in topological order and update the distance of all the adjacent vertices of the current vertex.
4. The distance of the adjacent vertex will be the maximum of the current distance and the distance of the current vertex plus the weight of the edge between the current vertex and the adjacent vertex.

```cpp
class Solution {
public:
    vector<int> longestPath(int V, vector<vector<int>>& edges, int s) {
        vector<vector<pair<int, int>>> adj(V);
        // here we have considered the weight of a given edge as 3rd element of the vector
        // each edge is represented as {u, v, w} where u is the source vertex, v is the destination vertex and w is the weight of the edge
        for (int i = 0; i < edges.size(); i++) {
            adj[edges[i][0]].push_back({edges[i][1], edges[i][2]});
        }

        vector<int> indegree(V, 0);
        for (int i = 0; i < V; i++) {
            for (auto& edge : adj[i]) {
                indegree[edge.first]++;
            }
        }

        queue<int> q;
        for (int i = 0; i < V; i++) {
            if (indegree[i] == 0) {
                q.push(i);
            }
        }

        vector<int> dist(V, INT_MIN);
        dist[s] = 0;

        while (!q.empty()) {
            int node = q.front();
            q.pop();

            for (auto& edge : adj[node]) {
                int next = edge.first;
                int weight = edge.second;
                dist[next] = max(dist[next], dist[node] + weight);
                indegree[next]--;
                if (indegree[next] == 0) {
                    q.push(next);
                }
            }
        }

        return dist;
    }
};
```

> Time Complexity: O(V+E)

Here first we are creating an adjacency list to store the graph.
Then we are creating an indegree array to store the indegree of each node.
Initialize the distance array with negative infinity and distance of source vertex as 0.
Now we will perform topological sort of the graph.

- Pop the front element of the queue and update the distance of all the adjacent vertices of the current vertex.
- The distance of the adjacent vertex will be the maximum of the current distance and the distance of the current vertex plus the weight of the edge between the current vertex and the adjacent vertex.
- If the indegree of the adjacent vertex becomes 0, push it into the queue.
- Return the distance array.

## 8. Topological Sort

Topological sorting of a Directed Acyclic Graph (DAG) is a linear ordering of vertices such that for every directed edge `u -> v`, vertex `u` comes before `v` in the ordering.

**Algorithm using DFS**:

1. Create a stack to store the topological order.
2. Create a visited array to keep track of the visited nodes.
3. For each node in the graph, if it is not visited, call the DFS function.
4. In the DFS function, mark the current node as visited and for each adjacent node, if it is not visited, call the DFS function recursively.
5. After visiting all the adjacent nodes, push the current node into the stack.

```cpp
class Solution {
public:
    void dfs(vector<vector<int>>& adj, vector<bool>& visited, stack<int>& st, int curr) {
        visited[curr] = true;

        for (int i = 0; i < adj[curr].size(); i++) {
            int next = adj[curr][i];
            if (!visited[next]) {
                dfs(adj, visited, st, next);
            }
        }

        st.push(curr);
    }

    vector<int> topologicalSort(int V, vector<vector<int>>& edges) {
        vector<vector<int>> adj(V);
        for (int i = 0; i < edges.size(); i++) {
            adj[edges[i][0]].push_back(edges[i][1]);
        }

        vector<bool> visited(V, false);
        stack<int> st;

        for (int i = 0; i < V; i++) {
            if (!visited[i]) {
                dfs(adj, visited, st, i);
            }
        }

        vector<int> res;
        while (!st.empty()) {
            res.push_back(st.top());
            st.pop();
        }

        return res;
    }
};
```

Here the top of the stack will be node with no outgoing edges.

**Time Complexity**: O(V+E)

**Algorithm using Indegree**:

1. Create an adjacency list to store the graph.
2. Create an indegree array to store the indegree of each node.
3. Create a queue to store the nodes with indegree 0.
4. Initialize the indegree array and the queue.
5. While the queue is not empty, do the following:
- Pop the front element of the queue and increment the count of visited nodes.
- Traverse all the adjacent nodes of the popped element and decrement their indegree.
- If the indegree of any adjacent node becomes 0, push it into the queue.
- If the count of visited nodes is not equal to the number of vertices, return an empty vector.
- Otherwise, return the topological order.

```cpp
class Solution {
public:
    vector<int> topologicalSort(int V, vector<vector<int>>& edges) {
        vector<vector<int>> adj(V);
        vector<int> indegree(V, 0);
        for (int i = 0; i < edges.size(); i++) {
            adj[edges[i][0]].push_back(edges[i][1]);
            indegree[edges[i][1]]++;
        }

        queue<int> q;
        for (int i = 0; i < V; i++) {
            if (indegree[i] == 0) {
                q.push(i);
            }
        }

        vector<int> res;
        int count = 0;

        while (!q.empty()) {
            int node = q.front();
            q.pop();
            res.push_back(node);
            count++;

            for (int i = 0; i < adj[node].size(); i++) {
                indegree[adj[node][i]]--;
                if (indegree[adj[node][i]] == 0) {
                    q.push(adj[node][i]);
                }
            }
        }

        return count == V ? res : vector<int>();
    }
};
```

- Here we are visiting each node once and each edge once.
**Time Complexity**: O(V+E)

> Topological sort is not unique. There can be multiple topological sorts for a given graph.

- They can be done only for Directed Acyclic Graphs (DAGs).

# 4. Bipartite Graphs

- This is an undirected graph.
- A bipartite graph is a graph whose vertices can be divided into two disjoint sets `U` and `V` such that every edge connects a vertex in `U` to a vertex in `V`.
- A bipartite graph is a graph that can be colored using two colors such that no two adjacent vertices have the same color.

**Algorithm to check if a given graph is bipartite using BFS**:

1. Assign color 0 to the source vertex and color 1 to all its adjacent vertices.
2. For each vertex, if it is not colored, assign the opposite color of its parent vertex.
3. If at any point, we find that the adjacent vertex has the same color as the current vertex, then the graph is not bipartite.

```cpp
class Solution {
public:
bool isBipartite(int V, vector<vector<int>>& edges) {
vector<vector<int>> adj(V);
        for (int i = 0; i < edges.size(); i++) {
            adj[edges[i][0]].push_back(edges[i][1]);
            adj[edges[i][1]].push_back(edges[i][0]);
        }

        vector<int> color(V, -1);
        queue<int> q;

        for (int i = 0; i < V; i++) {
            if (color[i] == -1) {
                q.push(i);
                color[i] = 0;

                while (!q.empty()) {
                    int node = q.front();
                    q.pop();

                    for (int j = 0; j < adj[node].size(); j++) {
                        int next = adj[node][j];
                        if (color[next] == -1) {
                            color[next] = 1 - color[node];
                            q.push(next);
                        }
                        else if (color[next] == color[node]) {
                            return false;
                        }
                    }
                }
            }
        }
        return true;
    }
};
```

**Time complexity**: O(V+E)
The above code works only if the graph is connected. If the graph is disconnected, then we need to call the above function for each connected component.

```cpp
class Solution {
    public:
    bool isBipartite(vector<int>&color, vector<vector<int>>& adj) {
        queue<int> q;

        for (int i = 0; i < V; i++) {
            if (color[i] == -1) {
                q.push(i);
                color[i] = 0;

                while (!q.empty()) {
                    int node = q.front();
                    q.pop();

                    for (int j = 0; j < adj[node].size(); j++) {
                        int next = adj[node][j];
                        if (color[next] == -1) {
                            color[next] = 1 - color[node];
                            q.push(next);
                        }
                        else if (color[next] == color[node]) {
                            return false;
                        }
                    }
                }
            }
        }
        return true;
    }

    bool isBipartiteGraph(int V, vector<vector<int>>& edges) {
        vector<vector<int>> adj(V);
        for (int i = 0; i < edges.size(); i++) {
            adj[edges[i][0]].push_back(edges[i][1]);
            adj[edges[i][1]].push_back(edges[i][0]);
        }

        vector<int>color(V, -1);
        for (int i = 0; i < V; i++) {
            if (color[i] == -1) {
                if (!isBipartite(color, adj)) {
                    return false;
                }
            }
        }
        return true;

    }
};
```


# 5. Disjoint Sets

A disjoint-set data structure maintians a collection `S` = { `S1`, `S2`, ..., `Sk` } of disjoint dynammic sets. To identify each set, choose a representative, which is some member of the set.

Each element of a set is represented by an object. Letting `x` denote the object, a disjoint-set supports the following opertations.

1. `make_set(x)`
2. `union(x,y)`
3. `find_set(x)`

## The Idea

Given a list of edges, we can find if two nodes are connected in `O(1)` amortised time using disjoint sets. 

1. Initially each node is in its own disjoint set and it is the representative element of itself. 
2. For every new edge, the disjoint sets are combined dynammically using the union operation and a representative element for the new set is chosen. 
3. This process is repeated till all the edges are processed.

| Edge processed | Collection of disjoint sets                      |
|----------------|--------------------------------------------------|
| initial sets   | {a}   {b}   {c} {d} {e} {f} {g} {h} {i} {j}      |
| (b,d)          | {a}   {b,d} {c}     {e} {f} {g} {h} {i} {j}      |
| (e,f)          | {a}   {b,d} {c}     {e,f}   {g} {h} {i} {j}      |
| (a,c)          | {a,c} {b,d}         {e,f}   {g} {h} {i} {j}      |
| (h,i)          | {a,c} {b,d}         {e,f}   {g} {h,i}   {j}      |
| (a,b)          | {a,b,c,d}           {e,f}   {g} {h,i}   {j}      |
| (f,g)          | {a,b,c,d}           {e,f,g}     {h,i}   {j}      |
| (b,c)          | {a,b,c,d}           {e,f,g}     {h,i}   {j}      |

Finally given n queries, of form `query(a,b)` where `a` and `b` are nodes in the graph, we can check if they are connected by calling `find_set(a)` and `find_set(b)` and checking if they have the same representative element.

## Implementations

### Naive Implementation

The naive implementation is a made by representing sets by rooted trees, with each node containing one member and each tree representing one set. In a disjoint-set forest, earch member points only to its parent. The root of each tree contains the representatitive and is its own parent.
```
    0             4
   / \           / \
  1   3         5   6
  |             |   |
  2             8   7
```

```cpp
void make_set(int v) {
    parent[v] = v;
}

int find_set(int v) {
    if (v == parent[v])
        return v;
    return find_set(parent[v]);
}

void union_sets(int a, int b) {
    a = find_set(a);
    b = find_set(b);
    if (a != b)
        parent[b] = a;
}
```

### Path Compression Optimisation and Union find by rank

It has to be noted that, though path compression and union find by rank reduce the overall complexity of the structure, it might not be suitable for certain classes of problems.

#### Path compression
If we call find_set(v) for some vertex v, we actually find the representative p for all vertices that we visit on the path between v and the actual representative p. The trick is to make the paths for all those nodes shorter, by setting the parent of each visited vertex directly to p.
```cpp
int find_set(int v) {
    if (v == parent[v])
        return v;
    return parent[v] = find_set(parent[v]);
}
```

#### Union find by rank
In this optimization we will change the union_set operation. To be precise, we will change which tree gets attached to the other one. In the naive implementation the second tree always got attached to the first one. In practice that can lead to trees containing chains of length  `O(n)` . With this optimization we will avoid this by choosing very carefully which tree gets attached.
```cpp
void make_set(int v) {
    parent[v] = v;
    rank[v] = 0;
}


void union_sets(int a, int b) {
    a = find_set(a);
    b = find_set(b);
    if (a != b) {
        if (rank[a] < rank[b])
            swap(a, b);
        parent[b] = a;
        if (rank[a] == rank[b])
            rank[a]++;
    }
}
```



## Applications of disjoint-set data structures

One of the many applications of disjoint-set data structures arises in determining the connected components of an undirected graph. When the edges of the graph are static, [depth first search](#2-depth-first-search-dfs) can compute the connected components faster. Sometimes, however, the edges are added dynammically, with the connected components updated as each edge is added. In this case, a disjoint-set can be more efficient than running a new depth-first search for each new edge or query.

### Additional problems

+ ![Colorful Arrays](https://www.spoj.com/problems/CLFLARR/)
+ ![Consecutive Letters](https://www.spoj.com/problems/CONSEC/)
+ ![Roads not only in Berland](http://codeforces.com/contest/25/problem/D)
