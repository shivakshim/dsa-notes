##  Why You Need **Inorder + (Pre OR Post)** to Uniquely Build a Binary Tree

## ⭐ Core Idea

A binary tree is **uniquely reconstructible** **only when the traversal set tells you exactly where the left subtree ends and the right subtree begins**.

**Inorder is the only traversal that gives this boundary.**

---

## ✅ Preorder + Inorder → Unique

- **Preorder** gives: `root`
- **Inorder** splits around the root:
    `[ left-subtree | root | right-subtree ]`
- Once left/right parts are known, the tree can be rebuilt uniquely.

---

## ✅ Postorder + Inorder → Unique

- **Postorder** gives: `root` (last element)
- **Inorder** again splits cleanly into left/right.
- Unique reconstruction is guaranteed.

---

## ❌ Preorder + Postorder → NOT Unique

- Neither traversal shows the exact boundary between left and right subtrees.
- Several different trees can produce the same pre & post traversals.

---

## 🎯 Final Summary

- **Inorder + Preorder → unique tree ✔️**
- **Inorder + Postorder → unique tree ✔️**
- **Preorder + Postorder → NOT guaranteed unique ❌**
- Reason: **Only inorder reveals clear left vs right subtree boundaries.**