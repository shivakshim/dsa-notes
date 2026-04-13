🔗[Problem link](https://www.interviewbit.com/problems/path-to-given-node/)

---

#### 🗝️Key Concept

- 

### 🧠Intuition/Approach

- 

### ❓Note

- 

### ⌛TC 
- Brute - 
- Optimized - 

### 📦SC
- Brute - O(1)
- Optimized - 

---

### ✅Solution

```cpp
bool getPath(TreeNode* root, int B, vector<int>& res){
    if(root == nullptr) return false;
    if(root->val == B){
        res.push_back(root->val);
        return true;
    }
    res.push_back(root->val);
    bool left = getPath(root->left, B, res);
    if(left == true) return true;
    bool right = getPath(root->right, B, res);
    if(right == true) return true;
    //not found
    res.pop_back();
    return false;
}
  res.push_back(root->val);
    bool left = getPath(root->left, B, res);
    if(left == true) return true;
    bool right = getPath(root->right, B, res);
    if(right == true) return true;
    //not found
    res.pop_back();
    return false;
}
```
 
 