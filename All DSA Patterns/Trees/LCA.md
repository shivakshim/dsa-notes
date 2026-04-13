-  We need to remember that the traversal will always reach the upper node first, in same tree or not.
-  Now there are just 3 options:
      1. It reached p which is in the left , q is underneath. Now since we just return the node we find, this will return p and nothing from right. But that's still correct because q is under p. So LCA is p.
      2. It reached p on right, and q is underneath it, Again, never reaches q but returns p. Still works because p is the LCA, returns nothing from left.
      3. p comes from left, never goes under p. But q is in right and so q comes from some right. Now we might even get q and p at different levels, but since we simply return p & q whenever we het them, at some root, we will get p from left as we all q from right, when this happens this root is the LCA, since this is the first root where both branches give p & q.



INT BST :
1. LCA is either the first root where they split . OR
2. The first node out of them both. 
- If they are in the same side of the root -> we must go further, root is definitely not the LCS, its juts an ancestor. The next root can be p / q, or the potential LCA.
- So when does this stop? Which node is the LCA? When they both stop being in the same side of the root.
- Because now they will both have separate parents if we move down further. If they become parts of separate subtrees, we stop. 