
# 🌳 **Trees — Interview Master Note 
[[💼Problems List]]

---

## ⭐ **What is a Tree?**

A hierarchical, non-linear data structure made of **nodes**. Unlike arrays or linked lists, trees represent **parent–child** relationships.

### Key Properties
- No cycles.
- Exactly **one root**.
- Every node has **0 or more children**.
- With `n` nodes, a tree has **n − 1 edges**.

---

# 🌲 **Binary Trees (BT)**
A tree where each node can have at most **two children** — left + right.

---

## 📌 **Types of Binary Trees**

### 1. **Full Binary Tree**
Each node has **0 or 2 children**.

### 2. **Complete Binary Tree**
Every level is filled except maybe the last; last level filled **left → right**.

### 3. **Perfect Binary Tree**
Every internal node has 2 children AND every leaf is at same depth.

### 4. **Balanced Binary Tree**
Height is `O(log n)`. AVL, Red-Black trees.

### 5. **Degenerate/Skewed Tree**
Basically a linked list.

---

# 🌳 **Binary Tree Traversals**

## DFS (Depth-First):

### 1. **Inorder** → Left, Node, Right
### 2. **Preorder** → Node, Left, Right
### 3. **Postorder** → Left, Right, Node
## BFS:
### 4. **Level Order Traversal**
Queue-based.

---

# 🧩 **Binary Tree Common Patterns**

## 🔹 **Recursive DFS Template (Most Important)**

```cpp
void dfs(TreeNode* root) {
    if(!root) return;

    // preorder: process here

    dfs(root->left);
    // inorder: process here

    dfs(root->right);
    // postorder: process here
}
```

```java
void dfs(TreeNode root) {
    if(root == null) return;

    // preorder
    dfs(root.left);
    // inorder
    dfs(root.right);
    // postorder
}
```

---

# 💥 **SUPER IMPORTANT INTERVIEW TOPICS**

## 1️⃣ **Height / Depth of Tree**

Recursive depth logic.

- `height = 1 + max(leftHeight, rightHeight)`
- Time: `O(n)`

## 2️⃣ **Diameter of Binary Tree**

Longest path between any 2 nodes.  
**Key formula:**

```
diameter = max(diameter, leftHeight + rightHeight)
```

## 3️⃣ **Balanced Binary Tree Check**

Return height, but return −1 if subtree unbalanced. Classic optimization.

## 4️⃣ **Invert Binary Tree** (mandatory)

Swap left/right.

## 5️⃣ **Symmetric Tree**

Check mirror property.

## 6️⃣ **Lowest Common Ancestor (LCA)**

DFS: return candidate nodes.

## 7️⃣ **Max Path Sum** (Hard)

Use DFS to compute max gain from each side and update global max.

## 8️⃣ **Root-to-Leaf Paths**

Path building using backtracking.

## 9️⃣ **Path Sum I, II, III** (VERY important patterns)

All variations of DFS + prefix-sum.

## 🔥 Prefix-Sum trick for Path Sum III

```
prefix[currSum - target]
```

HashMap-based.

## 🔟 **Serialize / Deserialize Binary Tree**

Level-order (most common). Preorder also works.

---

# 🌿 **Binary Search Tree (BST)**

A special binary tree where:

```
left < root < right
```

## Core Operations
- Insert (log n average)
- Search
- Delete (3 cases)

## Inorder Traversal of BST = Sorted

Used for
- checking validity
- converting BST → array
- Kth smallest

---

# 🔥 BST Interview Problems

- Validate BST
- LCA in BST (easy)
- Kth smallest/largest
- Delete node in BST (medium+)
- Sorted array → BST
- BST iterator

---

# 🍀 **Binary Tree vs Binary Search Tree Clarification**

|Feature|Binary Tree|BST|
|---|---|---|
|Structure|max 2 children|max 2 children|
|Ordering|none|left < root < right|
|Traversal|any|inorder = sorted|
|Use cases|generic, recursion|searching, ordering|

---

# 🌴 **Generic Tree (N-ary Tree) Section**

Not a binary tree.

### Node has **unlimited children**.

Used in:

- File systems
- Trie/Prefix Tree
- Organization charts
- Parsing structures (AST)

## Traversal Pattern

```cpp
void dfs(Node* root){
    if(!root) return;
    for(auto child : root->children){
        dfs(child);
    }
}
```

Key problems:

- N-ary preorder
- N-ary postorder
- Level order
- Max depth

---

# 🌴 **Binary Tree Full Code Template (C++ & Java)**

## **C++ Template**

```cpp
struct TreeNode {
    int val;
    TreeNode *left;
    TreeNode *right;
    TreeNode(int x) : val(x), left(NULL), right(NULL) {}
};

class Solution {
public:
    int solve(TreeNode* root) {
        if(!root) return 0;
        int left = solve(root->left);
        int right = solve(root->right);
        // do something
        return ...;
    }
};
```

## **Java Template**

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int x) { val = x; }
}

class Solution {
    int solve(TreeNode root) {
        if(root == null) return 0;
        int left = solve(root.left);
        int right = solve(root.right);
        // logic
        return ...;
    }
}
```

---

# 💡 **Tree Recognition — How to Identify the Pattern Quickly**

### 🔎 If the question asks:

- _"return height, check balance, compute something bottom-up"_ → **Postorder DFS**.
- _"root → left → right process order"_ → **Preorder DFS**.
- _"process sorted order, kth smallest/largest"_ → **Inorder DFS (BST)**.
- _"levels, nearest node, BFS, shortest path"_ → **Level Order / BFS**.
- _"paths, sums, backtracking"_ → **DFS + path vector**.
- _"longest path, max sum"_ → **DP on trees (postorder + global variable)**.

---

# 📌 Extra Note — **Not Binary Tree Questions**

These are trees but **NOT binary trees** 👇
- Trie (Prefix tree)
- N-ary Tree
- Segment Tree
- Fenwick Tree
- Disjoint Set / Union-Find (forest of sets)
- MST Trees (Kruskal/Prim result)


## **Recursion Stop-Rule ✨**

In recursion, we **don’t “continue” like in loops**. Instead:

- We define a **base case** that tells the function **when to stop recursing**.
- Think of it like:
>   “If the condition is NOT met, STOP here.”
- You **don’t write the condition for true**; you write the condition for **false**, because recursion naturally connues otherwise.
- Once the base case is hit, recursion **backs up and returns** — no explicit continue needed.

**TL;DR:** In recursion, you only need to say **when to stop**; everything else will naturally keep recursing.


---






































Solve this prefix sum IMP problem :[1248. Count Number of Nice Subarrays](https://leetcode.com/problems/count-number-of-nice-subarrays/)
