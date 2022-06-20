---
layout: default
use_math: true
title: Graph Representation
---

# Breadth First Traversal of a graph

The Breadth-first traversal or $BFS$ is a graph traversal algorithm that starts traversing the graph from a $source\ node$ and explores all of it's neighboring $nodes$ and all of their neighbouring $nodes$ and so on.

The idea is to use a $Queue$ to keep track of the neighbours from the $adjecency\ list$ and visit them while the $Queue$ is not empty.

```cpp
vector<int> GraphBFS(vector<int> adjecencyList[], int startNode, int nodeCount) {
  vector<bool> visited(nodeCount, false);
  queue<int> q;
  vector<int> bfsTraversal;

  visited[startNode] = true;
  q.push(startNode);
  
  while(!q.empty()) {
    int node = q.front();
    // process node
    bfsTraversal.push_back(node);
    q.pop();

    for(auto neighbour: adjecencyList[node]) {
      if(!visited[neighbour]) {
        visited[neighbour] = true;
        q.push(neighbour);
      }
    }
  }

  return bfsTraversal;
}
```

#### Time Complexity: $O(V + E)$
#### Space Complexity: $O(V)$

The above algorithm only works for $connected\ graph$, i.e., it traverses all the nodes for $connected\ graphs$ only. A generic $BFS$ algorithm is given below where it traverses all the $connected\ components$ of a $disconnected$ graph.

```cpp
vector<int> GenericGraphBFS(vector<int> adjecencyList[], int startNode, int nodeCount) {
  vector<bool> visited(nodeCount, false);
  vector<int> bfsTraversal;

  for(int i=0; i<nodeCount; ++i) {
    if(visited[i]) continue;
    queue<int> q;
    visited[i] = true;
    q.push(i);
    while(!q.empty()) {
      int node = q.front();
      // process node
      bfsTraversal.push_back(node);
      q.pop();

      for(auto neighbour: adjecencyList[node]) {
        if(!visited[neighbour]) {
          visited[neighbour] = true;
          q.push(neighbour);
        }
      }
    }
  }

  return bfsTraversal;
}
```

#### Time Complexity: $O(V + E)$
#### Space Complexity: $O(V)$
