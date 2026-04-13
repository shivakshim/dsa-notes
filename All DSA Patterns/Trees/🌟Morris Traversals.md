
🧠 Morris Traversal 

> Goal: Traverse a binary tree in **O(1) extra space** (no stack, no recursion) by being a little… sneaky 👀

---

## ✨ Big Idea (read this twice)

We **temporarily modify the tree** by creating a _fake right pointer_ (called a **thread**) so we can come back after finishing the left subtree.

Then we **clean it up**. No permanent damage. Pinky promise 🤞

---

## 🔗 What is a “thread”?

For a node `cur`:

- Go to its **left child**
- Find the **rightmost node** in that left subtree → call it `prev`

Two cases:

1. `prev->right == NULL` → create a thread
2. `prev->right == cur` → thread already exists → time to remove it

---

## 🧩 Why this works (intuition, not math)

Normally:
- Recursion / stack remembers where to return after left subtree

In Morris:
- The **thread** remembers that for you

Thread = “Hey future me, after you’re done left, come back here.”

---

## 🌱 Morris Inorder Traversal

### Rule

- **Visit when coming back from left*
### Steps
1. If `cur->left == NULL`
    - Visit `cur`
    - Move right
2. Else
    - Find `prev`
    - If `prev->right == NULL`
        - `prev->right = cur` (make thread)
        - Move left
    - Else
        - `prev->right = NULL` (remove thread)
        - Visit `cur`
        - Move right
### ✨ Code

```cpp
vector<int> inorderTraversal(TreeNode* root) {
    vector<int> res;
    TreeNode* cur = root;

    while(cur) {
        if(!cur->left) {
            res.push_back(cur->val);
            cur = cur->right;
        } else {
            TreeNode* prev = cur->left;
            while(prev->right && prev->right != cur)
                prev = prev->right;

            if(!prev->right) {
                prev->right = cur;
                cur = cur->left;
            } else {
                prev->right = NULL;
                res.push_back(cur->val);
                cur = cur->right;
            }
        }
    }
    return res;
}
```

---

## 🌸 Morris Preorder Traversal

### Rule
- **Visit BEFORE going left**
### Difference from inorder?
Only **WHEN you push `cur->val`** changes.
### Steps
1. If `cur->left == NULL`
    - Visit `cur`
    - Move right
2. Else
    - Find `prev`
    - If `prev->right == NULL`
        - Visit `cur` ✅ (this is the preorder magic)
        - `prev->right = cur`
        - Move left
    - Else
        - `prev->right = NULL`
        - Move right

### ✨ Code

```cpp
vector<int> preorderTraversal(TreeNode* root) {
    vector<int> res;
    TreeNode* cur = root;

    while(cur) {
        if(!cur->left) {
            res.push_back(cur->val);
            cur = cur->right;
        } else {
            TreeNode* prev = cur->left;
            while(prev->right && prev->right != cur)
                prev = prev->right;

            if(!prev->right) {
                res.push_back(cur->val);
                prev->right = cur;
                cur = cur->left;
            } else {
                prev->right = NULL;
                cur = cur->right;
            }
        }
    }
    return res;
}
```

---

## 🧨 The BIG confusion (and the truth)

> “Bro… `cur` is at `prev->right`. Why are we setting it to NULL first??”

### The truth 💥

- You already HAVE `cur`
- The thread’s job is DONE
- `prev->right = NULL` is just **cleanup**

You are NOT losing `cur`.  
You are **restoring the original tree**.

🧠 Think: _untie rope after crossing bridge_

---

## 🧷 One-liners to remember forever

- Thread = fake right pointer
- Create thread → go left
- See thread again → left subtree finished
- Remove thread → go right
- Morris = traversal + cleanup

---

## ⏱️ Complexity

- **Time**: `O(n)`
- **Space**: `O(1)` (no stack, no recursion, just ✨ audacity ✨)

---

### ➡️The Steps 
1. If there is no left : 
	  - This is the root, push it and go to right.
2. If left is present :
	  1. Move to the rightmost node of the left subtree. This move happens twice for each root, one before left and once after, in the after the right's right might already be the root, hence we need to move till either its next is null or current root.
	  2. Now if the rightmost's right is not the current root, it means the left has not been explored, so we connect the root to the right of the rightmost node, and then move the current root to odd left. Hence in this step the thread is created and control moves to left. now when left will be done, the rightmost will have the current and we can get back to root.
	  3. If the rightmost's right is the current node (how do we reach this rightmost? because whenever we are at a root, we always to its rightmost first) then the left is explored, so we simply push this root , and then make root = root->right.