1. in an ug, we cabn simply do by bfs with edge weights.
2. in DAG : 
-  if we ahve a DAG, and we wanna find using dfs : we fisrt do a topo sort and then on the stack we pop top, find the shortest oath to its adjacents and store it in tehir vis. 
- Thsi makes sure taht any node reached via the shoretst path because with topo we make sure all nodes preceeding a node have tehri shortest paths calculated and tyhen they ca;culate the shortest path to thsi node using that. Hence its guarntedd to be teh shortest.
- Why is topo needed in DAG with weighs :
		- in geenral BFS always reaches a node with teh shortets path, because we will obvisoulty reach nodes at earlier levels first. and that will be the shortest path to ir.
		- So when graph is unweighets or has unit weights, BFS works.
		- But when teh graph has weioghts, simple bfs will fail becase if we keep goung level wise we might reach the level with shortest path but highg weight, and then weven its next node's paths will be calcualted based on this. But supoose it is revidited by some node of later level, taht has less weighs , then now the weight of thsi node will be ypadtyed tahts fine, but its next nodes still acrry teh heiavy weighs. 
		- Henacse with a weighesd directed graph we need to do topo sort first , so that any node is only reached after all the precideing node;s shotest is found.
		- Ssme with dfs, even thought it will eventially give correct answer, i wil take too long, because everythime we are getting a  smaller ditance for a node, we need t recomplure all paths after it, and this miht be give tle.

| Graph type              | Edge weight | Best algo      |
| ----------------------- | ----------- | -------------- |
| Unweighted (UG/DG)      | All = 1     | BFS            |
| Weighted DAG            | Any         | Topo + DP      |
| Weighted graph (no neg) | Any         | Dijkstra       |
| Weighted graph (neg)    | Any         | Bellman-Ford   |
| DAG + DFS               | Any         | Works but slow |
Topo sort doesn’t make shortest paths possible —  
it makes them efficient.

| Graph type | Edge weights   | Correct algorithm              | dis[] |
| ---------- | -------------- | ------------------------------ | ----- |
| Undirected | all = 1        | **BFS** with queue<node, dis>  | yes   |
| Undirected | 0 or 1         | **0–1 BFS (deque)**            | yes   |
| Undirected | positive (any) | **Dijkstra**                   | yes   |
| Undirected | negative       | ❌ (use Bellman-Ford, but rare) | yes   |
