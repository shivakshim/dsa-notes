## What `union(u, v)` ACTUALLY means

**Union does NOT mean “add an edge.”**  
It means:

> “From now on, treat `u` and `v` as belonging to the **same connected component**.”

That’s it.

No physical edge.  
No graph structure.  
Just **set membership**.

---

## What DSU really stores

DSU only knows:

- a **representative (parent/root)** for each set
    
- which nodes belong to the same set
    

It does **NOT** store:

- adjacency
    
- paths
    
- neighbors
    
- weights
    

So when you do:

`union(u, v);`

You are saying:

> “Whether or not there’s a direct edge, these two nodes are now in the same group.”









- BY RANK - 
	1. Find ultimate parent of u and v : pu & pv.
	2. Find rank of pu, pv.
	3. Connect smaller rank to larger rank.

- By SIZE




