
# 🧠 Graph Theory — Complete Notes (Obsidian)

> **Purpose:** One-stop graph theory reference: concepts, intuition, representations, algorithms, patterns, templates, and interview cues.

recognistion:
1. matrix to chnage values/ search path
2. edges given.
3. states change with min transformation.
4. go from src to dst with shortest apth with k stops/no. of ways etc
5. shortest dist bwteten all cities/nodes
6. 

---

## 1. What is a Graph?

A **graph** is a set of **nodes (vertices)** connected by **edges**.

- **Vertices (V)**: entities (cities, cells, users, states)
    
- **Edges (E)**: relationships (roads, adjacency, transitions)
    

Graphs model _relationships_, not data itself.

---

## 2. Types of Graphs

### By Direction

- **Undirected**: edges have no direction (u—v)
    
- **Directed (Digraph)**: edges have direction (u → v)
    

### By Weight

- **Unweighted**: all edges equal
    
- **Weighted**: edges have cost/weight
    

### By Cycles

- **Acyclic**: no cycles
    
- **Cyclic**: contains cycles
    
- **DAG**: Directed Acyclic Graph
    

### By Connectivity

- **Connected** (undirected)
    
- **Disconnected**
    
- **Strongly Connected** (directed)
    
- **Weakly Connected** (directed)
    

### Special Graphs

- **Tree**: connected, acyclic, undirected
    
- **Forest**: collection of trees
    
- **Bipartite**: nodes split into 2 sets, no intra-set edges
    

---

## 3. Graph Representations (CRITICAL)

### 3.1 Adjacency List ✅ (Default Choice)

```cpp
vector<vector<int>> adj(V);
adj[u].push_back(v);
```

- Space: **O(V + E)**
    
- Traversal: **O(V + E)**
    
- Best for sparse graphs
    

### 3.2 Adjacency Matrix

```cpp
vector<vector<int>> adj(V, vector<int>(V));
adj[u][v] = 1;
```

- Space: **O(V²)**
    
- Edge check: **O(1)**
    
- Used when graph is dense or input is already matrix
    

### 3.3 Edge List

```cpp
vector<pair<int,int>> edges;
```

- Used for DSU, Kruskal
    
- Not good for traversal directly
    

---

## 4. 🔥 VERY IMPORTANT: Grid vs Adjacency Matrix

### Grid Graphs (Matrix stores **NODES**)

Examples:

- Rotten Oranges
    
- Number of Islands
    
- Flood Fill
    
- **Node = (i, j)** (coordinate)
    
- **grid[i][j] = state of node**
    
- Edges are **implicit** (up/down/left/right)
    

```cpp
int dr[4] = {-1,0,1,0};
int dc[4] = {0,1,0,-1};
```

### Adjacency Matrix (Matrix stores **EDGES**)

Examples:

- Number of Provinces
    
- isConnected[i][j]
    
- **i and j are node IDs**
    
- matrix[i][j] = edge existence
    

> 🔑 Rule:  
> If neighbors come from **geometry** → Grid Nodes  
> If neighbors come from **matrix values** → Edges

---

## 5. Degree Concepts

### Undirected Graph

- Degree of node = number of edges
    
- **Total degree = 2 × E**
    

### Directed Graph

- **In-degree** = incoming edges
    
- **Out-degree** = outgoing edges
    
- Sum of in-degrees = E
    
- Sum of out-degrees = E
    

---

## 6. BFS (Breadth First Search)

### When to Use

- Shortest path (unweighted)
    
- Level-wise traversal
    
- Multi-source problems
    

### Key Rule 🔥

> **Mark visited when you PUSH into queue**

### Template

```cpp
queue<int> q;
vector<int> vis(V,0);

q.push(src);
vis[src] = 1;

while(!q.empty()){
    int u = q.front(); q.pop();
    for(int v : adj[u]){
        if(!vis[v]){
            vis[v] = 1;
            q.push(v);
        }
    }
}
```

---

## 7. DFS (Depth First Search)

### When to Use

- Connectivity
    
- Cycle detection
    
- Topological sort
    
- SCCs
    

### Key Rule 🔥

> **Mark visited when you ENTER the node**

### Template

```cpp
void dfs(int u){
    vis[u] = 1;
    for(int v : adj[u]){
        if(!vis[v]) dfs(v);
    }
}
```

---

## 8. Connected Components

### Undirected Graph

- Run DFS/BFS from every unvisited node
    

### Directed Graph

- Weakly connected (ignore direction)
    
- Strongly connected → SCC algorithms
    

---

## 9. Cycle Detection

### Undirected Graph

```cpp
bool dfs(u, parent){
    vis[u]=1;
    for(v:adj[u]){
        if(!vis[v]){
            if(dfs(v,u)) return true;
        } else if(v != parent) return true;
    }
    return false;
}
```

### Directed Graph (3 colors)

- 0 = unvisited
    
- 1 = visiting (gray)
    
- 2 = visited (black)
    

Cycle exists if edge to gray node

---

## 10. Topological Sort (DAG only)

### DFS Method

- Push node after DFS finishes
    
- Reverse result
    

### Kahn’s Algorithm (BFS)

- Use in-degree
    
- Queue nodes with in-degree 0
    

---

## 11. Shortest Path Algorithms

|Algorithm|Graph|Weights|
|---|---|---|
|BFS|Unweighted|All = 1|
|Dijkstra|Weighted|No negative|
|Bellman-Ford|Weighted|Allows negative|
|Floyd-Warshall|Dense|Any|

---

## 12. Dijkstra (Adj List Preferred)

```cpp
priority_queue<pair<int,int>, vector<>, greater<>> pq;
pq.push({0,src});
```

- Time: O((V+E)logV)
    

---

## 13. Union Find (DSU)

Used for:

- Cycle detection (undirected)
    
- Connected components
    
- Kruskal MST
    

---

## 14. Minimum Spanning Tree

- **Kruskal** (edge list + DSU)
    
- **Prim** (adj list + PQ)
    

---

## 15. Strongly Connected Components

- **Kosaraju** (2 DFS)
    
- **Tarjan** (1 DFS, low-link)
    

---

## 16. Graph Patterns (INTERVIEW GOLD)

- Multi-source BFS (Rotten Oranges)
    
- BFS on grid
    
- Bipartite check (2-coloring)
    
- Shortest path in DAG
    
- Topo + DP
    
- Cycle detection
    

---

## 17. Common Interview Traps

❌ Mark visited on POP  
❌ Using matrix for large sparse graph  
❌ Forgetting disconnected components  
❌ Treating grid value as edge

---

## 18. Universal Graph Decision Rules

- Default → **Adjacency List**
    
- Grid input → **Grid BFS/DFS**
    
- Dense + small → **Matrix**
    
- Shortest path unweighted → **BFS**
    
- Weighted → **Dijkstra**
    

---

## 19. One-Line Truths (MEMORIZE)

- Visited = discovered, not processed
    
- BFS gives shortest path in unweighted graph
    
- Grid problems are implicit graphs
    
- Representation changes performance, not correctness
    

---

## 20. Mental Model Summary

> Graph = Nodes + Neighbors + Rules

How you store it is secondary.

---

## ✅ END OF GRAPH THEORY NOTES

> This file is designed for **Obsidian**. Add backlinks to:
> 
> - BFS
>     
> - DFS
>     
> - DSA Patterns
>     
> - System Design Graphs
>



- [x] [Word Search – LC 79](https://leetcode.com/problems/word-search/)       if there are multiple possible paths : backtrack, otherwise simple dfs.
- [ ] [Number of Islands – LC 200](https://leetcode.com/problems/number-of-islands/)
- [ ] [Max Area of Island – LC 695](https://leetcode.com/problems/max-area-of-island/)
- [ ] [Flood Fill – LC 733](https://leetcode.com/problems/flood-fill/)
- [ ] [Surrounded Regions – LC 130](https://leetcode.com/problems/surrounded-regions/)
- [ ] [Rotting Oranges – LC 994](https://leetcode.com/problems/rotting-oranges/)
- [ ] [Word Search II – LC 212](https://leetcode.com/problems/word-search-ii/)
- [ ] [Walls and Gates – LC 286](https://leetcode.com/problems/walls-and-gates/)
- [ ] [Shortest Path in Binary Matrix – LC 1091](https://leetcode.com/problems/shortest-path-in-binary-matrix/)
- [ ] [Pacific Atlantic Water Flow – LC 417](https://leetcode.com/problems/pacific-atlanti)
