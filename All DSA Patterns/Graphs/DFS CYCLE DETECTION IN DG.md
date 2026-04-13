- If a node has been previously visited but it isnt path visited, that means there's no cycle after that . Becuase if there it wold have returend a true and we woudlt even be chceking this path.
- If the node is eached from another branch, then we know taht beyond this teher is a cycle, hence it never goit backtracked.


