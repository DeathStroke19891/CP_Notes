# Table of Contents

| Sl. No. | Topic                                                       |
| ------- | ----------------------------------------------------------- |
| 1       | [Introduction to Trees](#1-introduction-to-trees)           |
| 2       | [Basic Terminologies](#basic-terminologies)                 |
| 3       | [Binary Tree](#3-binary-tree)                               |
| 4       | [Types of Binary Trees](#4-types-of-binary-trees)           |
| 5       | [Operations on Binary Trees](#5-operations-on-binary-trees) |
| 6       | [Binary Tree Traversals](#6-binary-tree-traversals)         |

# 1. Introduction to Trees

A tree is a non-linear data structure that is used to store data in a hierarchical manner. It is a collection of nodes connected by edges.

Each node will contain a data element and a list of references to other nodes (children).
There are different types of trees like Binary Tree, Binary Search Tree, AVL Tree, etc.
Trees are used to represent hierarchical data like file systems, organization structure, etc. Trees are a subset of Graphs.

## Basic Terminologies

- **Node**: A node is a basic unit of a tree. It contains data and references to other nodes.
- **Root**: The topmost node in a tree is called the root node.
- **Parent**: A node that has child nodes is called a parent node.
- **Child**: A node that is a descendant of another node is called a child node.
- **Leaf**: A node that does not have any child nodes is called a leaf node.
- **Edge**: The connection between two nodes is called an edge.
- **Height**: The height of a tree is the length of the longest path from the root node to a leaf node.
- **Depth**: The depth of a node is the length of the path from the root node to that node.
- **Level**: The level of a node is the depth of the node + 1.
- **Subtree**: A subtree is a tree that is part of a larger tree.
- **Binary Tree**: A tree in which each node has at most two children is called a binary tree.
- **Binary Search Tree**: A binary tree in which the left child is less than the parent node and the right child is greater than the parent node is called a binary search tree.
- **Balanced Tree**: A tree in which the height of the left and right subtrees of any node differ by at most one is called a balanced tree.
- **Complete Tree**: A binary tree in which all levels are completely filled except possibly for the last level, which is filled from left to right is called a complete tree.
- **Full Tree**: A binary tree in which each node has either 0 or 2 children is called a full tree.
- **Perfect Tree**: A binary tree in which all internal nodes have exactly two children and all leaf nodes are at the same level is called a perfect tree.
- **Traversal**: The process of visiting all the nodes in a tree is called traversal. There are three types of tree traversal: **_Inorder, Preorder, and Postorder_**.

# 3. Binary Tree

Binary tree is a data structure in which each node can have at most two children. The children are referred to as the left child and the right child. The left child is the child node that is on the left side of the parent node, and the right child is the child node that is on the right side of the parent node.

### Representation of Binary Tree

Each node in a binary tree contains three fields:

- **Data**: The data element stored in the node.
- **Left**: A reference to the left child node.
- **Right**: A reference to the right child node.

Example

```cpp
// Defining as a struct
struct node {
    int data;
    struct node* left;
    struct node* right;
};
// Defining as a class
class Node {
public:
    int data;
    Node* left;
    Node* right;
};
```

# 4. Types of Binary Trees

1. **On the basis of number of children** :
   - **Full Binary Tree**: A binary tree in which each node has either 0 or 2 children is called a full binary tree.
   - **Degenerate or Pathological Tree**: A binary tree in which each parent node has only one child is called a degenerate tree.
   - **Skewed Binary Tree**: A binary tree in which all the nodes have only one child is called a skewed binary tree.
2. **On the basis of Completion of Levels** :
   - **Complete Binary Tree**: A binary tree in which all levels are completely filled except possibly for the last level, which is filled from left to right is called a complete binary tree.
   - **Perfect Binary Tree**: A binary tree in which all internal nodes have exactly two children and all leaf nodes are at the same level is called a perfect binary tree.
   - **Balanced Binary Tree**: A binary tree in which the height of the left and right subtrees of any node differ by at most one is called a balanced binary tree.
3. **On the basis of Node Values** :
   - **Binary Search Tree**: A binary tree in which the left child is less than the parent node and the right child is greater than the parent node is called a binary search tree.
   - **AVL Tree**: A binary search tree in which the height of the left and right subtrees of any node differ by at most one and the left and right subtrees are also AVL trees is called an AVL tree.
   - **Red-Black Tree**: A binary search tree in which each node is colored either red or black and the root node is always black is called a red-black tree.
   - **B-Tree**: A self-balancing tree in which each node can have more than two children is called a B-tree.
   - **B+ Tree**: A self-balancing tree in which each node can have more than two children and all the data is stored in the leaf nodes is called a B+ tree.
   - **Segment Tree**: A tree used for storing intervals or segments is called a segment tree.

# 5. Operations on Binary Trees

1. **Insertion**: Insert a new node in the binary tree.
   We can insert a node anywhere in the binary tree by inserting the node as a left or right child of any node OR by making it the root of the tree.

- **Algorithm to insert a node in a Binary Tree**
  - Check if there is a node whose left child is NULL, then insert the new node as the left child of that node.
  - Check if there is a node whose right child is NULL, then insert the new node as the right child of that node.
  - If no such nodes are found then find a leaf node and insert the new node as the left child of that node.

2. **Tree Traversals** :

- Depth First Traversals:
  - Inorder (Left, Root, Right)
  - Preorder (Root, Left, Right)
  - Postorder (Left, Right, Root)
- Breadth First Traversal:
  - Level Order Traversal

3. **Deletion**: We can delete any node from the binary tree and rearrange the nodes after deletion to again form a valid binary tree.

- **Algorithm to delete a node from a Binary Tree**

  - Find the node to be deleted.
  - If the node has no children, then simply delete the node.
  - If the node has one child, then replace the node with its child.
  - If the node has two children, then find the inorder successor of the node, replace the node with the inorder successor, and delete the inorder successor.

- Inorder Successor: The inorder successor of a node is the node with the smallest key greater than the key of the given node.

4. **Searching**: We can search for a node in a binary tree by traversing the tree and comparing the key of each node with the key we are searching for.

- **Algorithm to search for a node in a Binary Tree**
  - Start from the root node.
  - If the key of the current node is equal to the key we are searching for, then return the current node.
  - If the key of current node is not equal to the key we are searching for, then recursively search in the left and right subtrees.
  - If the key is not found in the tree, then return NULL.

# 6. Binary Tree Traversals

## 1. Inorder Traversal

In inorder traversal, the nodes are recursively visited in this order: left, root, right.

```cpp
void inorder(Node* root) {
    if (root == NULL) return;
    inorder(root->left);
    cout << root->data << " ";
    inorder(root->right);
}
```

## 2. Preorder Traversal

In preorder traversal, the nodes are recursively visited in this order: root, left, right.

```cpp
void preorder(Node* root) {
    if (root == NULL) return;
    cout << root->data << " ";
    preorder(root->left);
    preorder(root->right);
}
```

## 3. Postorder Traversal

In postorder traversal, the nodes are recursively visited in this order: left, right, root.

```cpp
void postorder(Node* root) {
    if (root == NULL) return;
    postorder(root->left);
    postorder(root->right);
    cout << root->data << " ";
}
```

## 4. Reverse inorder Traversal

In reverse inorder traversal, the nodes are recursively visited in this order: right, root, left.

```cpp
void reverseInorder(Node* root) {
    if (root == NULL) return;
    reverseInorder(root->right);
    cout << root->data << " ";
    reverseInorder(root->left);
}
```

## 5. Level Order Traversal

In level order traversal, the nodes are visited level by level from left to right.
We will be using a queue to store the nodes at each level.

```cpp
void levelOrder(Node* root) {
    if (root == NULL) return;
    queue<Node*> q;
    q.push(root);
    while (!q.empty()) {
        Node* current = q.front();
        cout << current->data << " ";
        if (current->left != NULL) q.push(current->left);
        if (current->right != NULL) q.push(current->right);
        q.pop();
    }
}
```

## 6. Spiral Order Traversal

In spiral order traversal, the nodes are visited level by level in a zigzag manner.

Lets say the tree is like this:

```
        1
       / \
      2   3
     / \ / \
    7  6 5  4
```

Then the spiral order traversal will be: 1 3 2 7 6 5 4

```cpp
void spiralOrder(Node* root) {
    if (root == NULL) return;
    stack<Node*> s1, s2;
    s1.push(root);
    while (!s1.empty() || !s2.empty()) {
        while (!s1.empty()) {
            Node* current = s1.top();
            s1.pop();
            cout << current->data << " ";
            if (current->right != NULL) s2.push(current->right);
            if (current->left != NULL) s2.push(current->left);
        }
        while (!s2.empty()) {
            Node* current = s2.top();
            s2.pop();
            cout << current->data << " ";
            if (current->left != NULL) s1.push(current->left);
            if (current->right != NULL) s1.push(current->right);
        }
    }
}
```

## 7. Morris Traversal

Morris traversal is an efficient way to traverse a binary tree without using any extra space. It is based on the concept of threading.

```cpp
void morrisInorder(Node* root) {
    Node* current = root;
    while (current != NULL) {
        if (current->left == NULL) {
            cout << current->data << " ";
            current = current->right;
        } else {
            Node* predecessor = current->left;
            while (predecessor->right != NULL && predecessor->right != current) {
                predecessor = predecessor->right;
            }
            if (predecessor->right == NULL) {
                predecessor->right = current;
                current = current->left;
            } else {
                predecessor->right = NULL;
                cout << current->data << " ";
                current = current->right;
            }
        }
    }
}
```

## 8. Vertical Order Traversal

Vertical order traversal is a traversal in which nodes are visited level by level in a vertical order.

Lets say the tree is like this:

```
        1
       / \
      2   3
     / \ / \
    4  5 6  7
```

Then the vertical order traversal will be: 4 2 1 5 6 3 7
A map is used to store the nodes at each horizontal distance from the root node.
A queue is used to perform the BFS traversal. Each element in the queue is a pair of the node and its horizontal distance from the root.

The front of the queue is popped and the node is inserted into the map at the corresponding horizontal distance.
Then the left child is pushed into the queue with a horizontal distance of hd - 1 and the right child is pushed into the queue with a horizontal distance of hd + 1.

After the traversal is complete, the nodes are printed from the map in ascending order of the horizontal distance.

```cpp
void verticalOrder(Node* root) {
    map<int, vector<int>> m;
    queue<pair<Node*, int>> q;
    q.push({root, 0});
    while (!q.empty()) {
        Node* current = q.front().first;
        int hd = q.front().second;
        q.pop();
        m[hd].push_back(current->data);
        if (current->left != NULL) q.push({current->left, hd - 1});
        if (current->right != NULL) q.push({current->right, hd + 1});
    }
    for (auto it = m.begin(); it != m.end(); it++) {
        for (int i = 0; i < it->second.size(); i++) {
            cout << it->second[i] << " ";
        }
    }
}
```

## 9. Diameter of a Binary Tree

Diameter of a binary tree is the number of nodes on the longest path between two leaves in the tree.

Lets say the tree is like this:

```
        1
       / \
      2   3
     / \ / \
    4  5 6  7
```

Then the diameter of the tree will be 5 (4 -> 2 -> 1 -> 3 -> 7)

```cpp
int diameterOfTree(Node* root, int& diameter) {
    if (root == NULL) return 0;
    int leftHeight = diameterOfTree(root->left, diameter);
    int rightHeight = diameterOfTree(root->right, diameter);
    diameter = max(diameter, leftHeight + rightHeight);
    return 1 + max(leftHeight, rightHeight);
}
```

## 10. Height of a Binary Tree

Height of a binary tree is the length of the longest path from the root node to a leaf node.

```cpp
int heightOfTree(Node* root) {
    if (root == NULL) return 0;
    return 1 + max(heightOfTree(root->left), heightOfTree(root->right));
}
```

## 11. Lowest Common Ancestor

Lowest Common Ancestor (LCA) of two nodes in a binary tree is the lowest node that has both the nodes as its descendants.

Lets say the tree is like this:

```
        1
       / \
      2   3
     / \ / \
    4  5 6  7
```

Then the LCA of 4 and 5 will be 2.
LCA of 5 and 7 is 1.

The following code snippet finds the LCA of two nodes in a binary tree.
First, we check if the root is NULL or if the root is one of the nodes we are looking for.
Then we recursively find the LCA in the left and right subtrees.

- If we take the p =4 and q = 5
- First call will be lowestCommonAncestor(1, 4, 5)
- Second call will be lowestCommonAncestor(2, 4, 5)
- Third call will be lowestCommonAncestor(4, 4, 5) which will return 4
- Fourth call will be lowestCommonAncestor(5, 4, 5) which will return 5
- Then the left will be 4 and right will be 5, so since both are not NULL, we return the root which is 2.
- For the first call the left will be 2 and right will be null, so we return 2.

```cpp
Node* lowestCommonAncestor(Node* root, Node* p, Node* q) {
    if (root == NULL || root == p || root == q) return root;
    Node* left = lowestCommonAncestor(root->left, p, q);
    Node* right = lowestCommonAncestor(root->right, p, q);
    if (left == NULL) return right;
    if (right == NULL) return left;
    return root;
}
```
