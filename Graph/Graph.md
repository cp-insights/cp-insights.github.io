---
layout: default
use_math: true
title: Graph
---

# Graph

A $Graph$ is a data structure composed of $nodes$ and $edges$. 
A $Node$ is a finite set of vertices. 
A $Edge$ is an ordered pair of vertices 
of the form $(u, v)$.

```cpp
struct Edge {
  int u, v;
  Edge(int u, int v): u(u), v(v) {}
};

struct Graph {
  int nodeCount;
  vector<Edge> edges;
  Graph(int n): nodeCount(n) {}
  Graph(int n, vector<Edge> edges): nodeCount(n), edges(edges) {}
  void addEdge(int u, int v) {
    edges.push_back({u, v});
  }
};
```

A $directed\ graph$ is a graph which contains $directed\ edges$. 
A $directed\ edge$ is an ordered pair
$(u, v)$ which represents an edge in the direction from $u$ to $v$.

```cpp
graph.addEdge({u, v});
```

An $undirected\ graph$ is a graph which contains $undirected\ edges$.
An $undirected\ edge$ is a pair
$(u, v)$ which represents an edge in from $u$ to $v$ and $v$ to $u$. 
The $undirected\ edges\ (u, v)$ 
and $(v, u)$ are identical.

```cpp
graph.addEdge({u, v});
graph.addEdge({v, u});
```

A $weighted\ graph$ is a graph with $weighted\ edges$.
A $weighted\ edge$ is a triplet 
$(u, v, w)$ which represents an edge from $u$ to $v$ having a weight/cost/value of $w$.

```cpp
struct WeightedEdge {
  int u, v, w;
  WeightedEdge(int u, int v, int w): u(u), v(v), w(w) {}
};

struct WeightedGraph {
  int nodeCount;
  vector<WeightedEdge> edges;
  WeightedGraph(int n): nodeCount(n) {}
  WeightedGraph(int n, vector<WeightedEdge> edges): nodeCount(n), edges(edges) {}
  void addEdge(int u, int v, int w) {
    edges.push_back({u, v, w});
  }
}
```

A $node\ labelled\ graph$ is a graph in which consists of $labelled\ vertices$.
A $labelled\ node$ is a node $u$ with an associated label/value $x$.

```cpp
struct LabelledNode {
  int id;
  int value; // can be of any type
  LabelledNode(int id, int value): id(id), value(value) {}
};

struct LabelledEdge {
  LabelledNode u, v;
  LabelledEdge(LabelledNode u, LabelledNode v): u(u), v(v) {}
};

struct NodeLabelledGraph {
  int nodeCount;
  vector<LabelledNode> edges;
  NodeLabelledGraph(int n): nodeCount(n) {}
  NodeLabelledGraph(int n, vector<NodeLabelledGraph> edges): nodeCount(n), edges(edges) {}
  void addEdge(LabelledNode u, LabelledNode v) {
    edges.push_back({u, v});
  }
};
```

A $cyclic\ graph$ is a $directed\ graph$ with at least one $cycle$.
A $cycle$ is a path along $directed\ edges$ from a $node$ to itself.
A $directed\ acyclic\ graph$, commonly known as $DAG$ is a graph without cycle. 
A $tree$ is a type of $directed\ acyclic\ graph$.

### Learn more:

1. [Graph Representation](/Graph/GraphRepresentation.md)