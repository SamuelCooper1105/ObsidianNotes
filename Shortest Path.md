Weight of a path is a summation of all the weights in the path
We are given a directed graph G, and a weight function w: E -> R
weight of path p = $<v_0, v_1,\dots, v_k>$ and $w(p) = \sum_{i=1}^{k} w(v_{i-1}, v_i)$

Find the shortest path from a source vertex to every other vertex.

For an unweighted case 


All Pairs Shortest path.
Find the shortest paht between every pair of vertices
unweighted graph
- run BFS algorithh |V| times: O(VE)
Nonnegative edge weights:
-run Dijisktra's algorithm |V| times: O(V E log V) 
Cases 1 and 2 cannot be improved upon a lot, however if we consider a more general case. we can greatly improve it. 
So if we have an input  of a directed graph $G=(V,E)$ where $V ={1,2, \dots,n}$, with edge weight function $w: E->R$ 
We want to find a $n *n$ matrix of shortest path- lengths $\phi 
we can improve this using [[Dynamic Programming]]. Recall the structure of a dynamic programming structure <details> <summary>Dynamic Programming</summary> ![[Dynamic Programming#What is Dynamic Programming?]] </details>
