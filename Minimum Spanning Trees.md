The goal here is to find a spanning tree using edges that minimize the total weight, where the weight is the numerical value of the edges or vertices of the graph,[[Graphs]]. It focuses primarily on finding the most effecient way to connect all the nodes in a graph. so Akin to DPS or BFS. 
- Spanning tree: a tree(i.e. a connected acyclic graph) which contains all the vertices of the graph.
- spanning forest: if a graph is not connected, then there is a spanning tree for e ach connet3ed componenet of the graph , 
We want the tree to have all the vertices and |V| -1 edges.

A minimum spanning tree is not unique, MST has no cycles. A MST also has no cycles, so if we had a graph that was a cycle and wanted to find the MST we could imply remove an edge and we would still have all the vertices connected while reducing the cost. Thus the number of edges in a MST is $$|V|-1$$

So how might we grow a MST? 
-  start with growing a set, A,  of edges( initially empty)
- Incrementally add edges to A such that they would belong to an MST. So what if we only added safe edges.
- An edge (u, v) is safe for A if and only if $A \cup (u, v)$ is also a subset of some MST. 
So how do we find as a safe edge for each iteration. 
Here are some definition that may help us solve these kinds of problems.
- cut: a cut is a partition of vertices into disjoint sets S and V - S.
- an edge crosses the cut (S, V-A) if one endpoint is in S and the other is in V-S
- A cut respects a set A of edges if no edge in A crosses the cut.
- an edge is a light edge crossing a cutif its weight is minimum over all edges crossing the cut.


So what might some applications be for minimum spannign trees?
IMagine we have a tree

## Prim's Algorithm

## Kruskal's Algorithm
