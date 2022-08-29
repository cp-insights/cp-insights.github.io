---
layout: default
use_math: true
title: Graph Representation
---

# Graph Representation

An $Edge\ List$ is the canonical way of representing a graph. 

If the graph is not a weighted graph, it is a list of pairs 
$(u, v)$ representing an edge from node $u$ to $v$. 

```cpp
struct Edge {
  int u, v;
  Edge(int u, int v): u(u), v(v) {}
};
vector<Edge> edgeList;
```

If the graph is a weighted graph, it is a list of pairs
$(u, v, w)$ representing a weighted edge from $u$ to $v$ with a weight $w$.

```cpp
struct WeightedEdge {
  int u, v, w;
  WeightedEdge(int u, int v, int w): u(u), v(v), w(w) {}
};
vector<WeightedEdge> edgeList;
```

An $Adjecency\ List$ is a mapping of $nodes$ to it's $adjecent$ nodes. Two $nodes$ are said to be $adjecent$ if there exists an $edge$ between them.

```cpp
vector<int> adjecencyList[nodeCount];
for(Edge edge: edges) {
  adjecencyList[edge.u].push_back[edge.v];
}
```

An $Adjecency\ Matrix$ of an unweighted graph is a matrix of size $N \times N$ (where $N$ is the node count) in which each value at index $(u, v)$ is $0$ or $1$, where $0$ represents the absence of an edge and $1$ represents the presence of an edge.

```cpp
int adjecencyMatrix[nodeCount][nodeCount]; 
memset(adjecencyMatrix, 0, nodeCount * nodeCount * sizeof(int));
for(Edge edge: edges) {
  adjecencyMatrix[edge.u][edge.v] = 1;
}
```

An $Adjecency\ Matrix$ of a weighted graph is a matrix of size $N \times N$ (where $N$ is the node count) in which each value at index $(u, v)$ is $0$ or $w$, where $0$ represents the absence of an edge and $w$ represents the weight of the edge.

```cpp
int adjecencyMatrix[nodeCount][nodeCount]; 
memset(adjecencyMatrix, 0, nodeCount * nodeCount * sizeof(int));
for(WeightedEdge edge: edges) {
  adjecencyMatrix[edge.u][edge.v] = edge.w;
}
```
