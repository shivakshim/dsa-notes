1. DFS
- Anyone who is a part of the cycle cannot be a safe node.
- Anyone who has an outgoing edge into the cycle can never be a safe node.


1. BFS : 
- We will sue reverse of topo sort for this.
- Here we arent concenred about the indegree but teh outdegree.
- We basically want all the nodes that either have outdegree as 0, or are connected to only nodes that are conected to terminal nodes taht ahve putdegree 0.
- We here we can start with the nodes that are termilar outdegree 0, ab=nd then keep going bcak and find all nodes that are only connected to (have outdegrees to) safe/termilar nodes.
- For thsi we reverse teh graph.
- Now all teh nodes that have indegrees coming form terminal nodes and decremneted, and checked if tehy ahve indegree 0 now : which will men all nodes they were connecte dto were safe/termilar :  meaning tehty are safe too.
- If it does not beciem 0, it means they are conencetd to a node taht;s part of acycle, or it is a part of teh ceyecle.( that means in reevrse this cycel has an outdegree to it , or in og, it had an outdegree to cycel).
- if a node doesntahve an outdegere(in og) to any cycel, then after reeversing, it will have indegrees coing only deom the terminals, hece making it safe, but if it otriianly had an outdefree to the cycel, then after reverseing it willl get an indegree from ctccke too, making it never 0, and this never safe.