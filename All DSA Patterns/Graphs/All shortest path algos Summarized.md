| Graph Type                      | Cycles Allowed? | Topological Order Exists? | Natural Order Used      | Distance Finalized When     | Algorithm        | Time           |
| ------------------------------- | --------------- | ------------------------- | ----------------------- | --------------------------- | ---------------- | -------------- |
| **Unweighted / Unit weight**    | ✅ Yes           | ❌ No                      | BFS levels (edge count) | First visit                 | **BFS**          | **O(V + E)**   |
| **0 / 1 weights**               | ✅ Yes           | ❌ No                      | Deque (0-edge first)    | First pop                   | **0–1 BFS**      | **O(V + E)**   |
| **DAG (any weights)**           | ❌ No            | ✅ Yes                     | Topological order       | After all parents processed | **Topo + Relax** | **O(V + E)**   |
| **Weighted (non-negative)**     | ✅ Yes           | ❌ No                      | Min-distance first (PQ) | When popped from PQ         | **Dijkstra**     | **O(E log V)** |
| **Weighted (negative allowed)** | ✅ Yes           | ❌ No                      | No safe order           | After N−1 relaxations       | **Bellman-Ford** | **O(V · E)**   |
