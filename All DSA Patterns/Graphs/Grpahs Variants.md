1. Connected componenets.
2. Fill, spread, etc : bfs .
3. island/encalves(boundary constraints) : bfs/dfs on edge nodes , mark all the nodes connecetd to them safe and then chage the remaning ones(not connected to oundary in any way).
4. Word ladder : starte transformations, in least steps :  bfs on each transformed state.
5. Unqie componenets : stiore coponent shapeb in a set(will only keep unqiue shapes) by traversing comnpoenets and storyingnodes by substrating teh root .
6. WE know for sure its a DAG - DFS topo.
7. We need to detect if it possible yto have topo(no cyecl) + find topo, -> kahn's / BFS Topo.
8. Only detect cycle : DFS : vis+path vis + backtrack vis path
9. 