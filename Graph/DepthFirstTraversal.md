---
layout: default
use_math: true
title: Graph Representation
---

# Depth First Traversal of a graph

Depth-first search or $DFS$ is an algorithm for traversing or searching tree or graph data structures. The algorithm starts at a $source\ node$ and explores as far as possible along each branch before $backtracking$.

```cpp
vector<int> GraphDFS(vector<int> adjacencyList[], int startNode, int nodeCount) {
  vector<bool> visited(nodeCount, false);
  vector<int> dfsTraveral;
  GraphDFS(adjacencyList, startNode, nodeCount, visited, dfsTraversal);
  return dfsTraversal;
}

vector<int> GraphDFS(vector<int> adjacencyList[], int startNode, int nodeCount, vector<bool> visited, vector<int> dfsTraversal) {
  visited[startNode] = true;
  dfsTraversal.push_back(startNode);

  for(int neighbour: adjacencyList[startNode]) {
    if(!visited[neighbour])
      GraphDFS(adjacencyList, startNode, nodeCount, visited, dfsTraversal);
  }
}
```

#### Time Complexity: $O(V + E)$
#### Space Complexity: $O(V)$

The above algorithm only works for $connected\ graph$, i.e., it traverses all the nodes for $connected\ graphs$ only. A generic $BFS$ algorithm is given below where it traverses all the $connected\ components$ of a $disconnected$ graph.

```cpp
vector<int> GenericGraphDFS(vector<int> adjacencyList[], int nodeCount) {
  vector<bool> visited(nodeCount, false);
  vector<int> dfsTraveral;
  for(int i=0; i<nodeCount; ++i) {
    if(!visited[i])
      GraphDFS(adjacencyList, i, nodeCount, visited, dfsTraversal);
  }
  return dfsTraversal;
}

vector<int> GenericGraphDFS(vector<int> adjacencyList[], int startNode, int nodeCount, vector<bool> visited, vector<int> dfsTraversal) {
  visited[startNode] = true;
  dfsTraversal.push_back(startNode);

  for(int neighbour: adjacencyList[startNode]) {
    if(!visited[neighbour])
      GraphDFS(adjacencyList, startNode, nodeCount, visited, dfsTraversal);
  }
}
```

#### Time Complexity: $O(V + E)$
#### Space Complexity: $O(V)$
