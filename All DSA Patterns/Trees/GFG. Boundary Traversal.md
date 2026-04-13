🔗[Problem link](https://www.geeksforgeeks.org/problems/boundary-traversal-of-binary-tree/1)

---

#### 🗝️Key Concept

1. 👈**Left Boundary**   : keep taking left from root, if no left -> take right, except leaf.
2. 👉**Right Boundary** : keep taking right from root, if no right -> take left, except leaf (in reverse).
3. 🌿**Leaf boundary**   : Inorder traversal to take just the leaf nodes.

### 🧠Intuition/Approach

- **Add root** to result.
- **Traverse down the left side** (prefer left child; skip leaves).
- **Collect all leaves** using full DFS.
- **Traverse down the right side** (prefer right child; skip leaves) and push values into a stack.
- **Pop stack into result** to reverse the right boundary.

### ❓Note

- We push root first, and then send root-> left for left boundary and root->right for right boundary.
- Because of this, we need to have a null check and a leaf node check as the base in methods.

### ⏱ **Time Complexity (TC)**

**O(N)**  
Every node is touched at most once across the left boundary, leaf DFS, or right boundary.

### 💾 **Space Complexity (SC)**

**O(H)** → height of tree  
Comes from recursion stack + the right-boundary stack.  
Worst case (skewed tree): **O(N)**.  
Best case (balanced tree): **O(log N)**.

---

### ✅Solution

```cpp
   void getLeft(Node* root, vector<int>& res){
        if(root == nullptr) return;        
        if(root->left == nullptr && root->right == nullptr) //leaf node
         return;
        
        res.push_back(root->data);
        if(root->left) getLeft(root->left, res);
        else getLeft(root->right, res);
    }
    
    void getLeaf(Node* root, vector<int>& res){
        if(root == nullptr) return;        
        if(root->left == nullptr && root->right == nullptr){ //leaf node
            res.push_back(root->data);
            return;
        }
        
        getLeaf(root->left, res);
        getLeaf(root->right, res);
    }
    
    void getRight(Node* root, stack<int>& st){
        if(root == nullptr) return;        
        if(root->left == nullptr && root->right == nullptr) 
         return;
         
        st.push(root->data);
        if(root->right) getRight(root->right, st);
        else getRight(root->left, st);
    }
    
    vector<int> boundaryTraversal(Node *root) {
        // code here
        vector<int> res;
        if(root == nullptr) return res;
        if(root->left == nullptr && root->right == nullptr) {
            res.push_back(root->data);
            return res;
        }
        res.push_back(root->data);
        
        getLeft(root->left, res);
        getLeaf(root, res);
 
        stack<int> st;
        getRight(root->right, st);
        while(!st.empty()){
            res.push_back(st.top());
            st.pop();
        }
        
        return res;
    }
```
 
 