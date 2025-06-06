
#### Strongly Connected
so we can have undirected graphs:
A connected graph is when every pair of vertices is connected by a path. Connected components are all possible connected subgraphs. 
we can also have directed graphs.
Strongly connected graphs are wehre every two verticds are reachable from each other, and strongly connectted compnotents which is when all sosible stronly connected subgraphs.

## Trees 
A tree is a connected, acyclic undirected graph, see the following for more information. [[Minimum Spanning Trees]], [[Binary Search Trees]], [[Red-Black Trees]]

## BiPartite Graph
A bipartite graph is an undirected graph $G=(V,E)$ in which $V_1 + V_2$ and there edges only between vertices in $V_1$ and $V_2$. 
### Implementation
we have two standard ways of implementing graphs
1. Adjancency List:
	- An Array of $|V|$ lists, one for each vertex in V
	- Each List $Adj[u]$ contains all the vertices v that are adjacent to u, or in other eords there is an edge from u to v.
	- Can be used for both directed and undirected graphs.
	Properties of an adjancey List repressentation
	- Sum of lengths of all adjancy lists
	- DIrected graph$|E|$ 
		- edge(u,v) appears only once 
	- Undirected graph:$2|E|$ 
		- edge (u,v) appears twice 
	- Or in other words for directe graph an edge appearrs only once, and in an undircted graph the edge appears twice. 
	The memory require is $\Theta(V+E)$, and preferred when the graph is sparse $|E| <<|V| ^2$ we need to wuickly determien the ndeos adjacent to a given ndoe.
	Some Disdavantages of these are that theresi no wuick way to determine if (u,v) is in E. The time to lists all the vertics adjacent to u, is $\theta (degree(u))$ 
2. Adjancy MAtrix:
	- Assume that all the vertices are numbered 1,2,...|V| 
	- The representation consists of a matrix $A_{|V| x|V|}$ : for $$
a_{ij} =
\begin{cases} 
1, & \text{if } (i,j) \text{ is an element of } E \\ 
0, & \text{otherwise} 
\end{cases}
$$

### Depth First Search:
When we implement Depth First Search search for a graph we are traversing every adajcent vertice one by one. WHen we traverse an adjacent vertex we completly finish the traverasl of all ertices reachable through taht adjacent vertex. 
So we want to start at the root node. the root node here being some arbitary node in the case of a graph. Then search the vertices that can be explored as far as long as that branch, in other words we are trying to search as deep as possible. It is also a stragy to search or solve a maze. %%This dude, Charles Pierre Trumeaux used it for this purpose in the 19th century.%%
TIme and space cimpelxity both vary depending on usage cases, but in theortical computer science, DFS is typically used to traverse an entire graph, and as such takes $O(|V| +|E|$ ) where |V| is the nunber of vertcies and |E| is the number of edges. THis is lienar in the size of graph. IN these applicatiosn it also used space O(|V|) in the worst acse to store the stack of vertives on the current search path as well as the set of already visited vertices. THis in this particualr setting time and space boudns are the same as BREdth FIrst Search. 

#### Applications 
DFS can be used to perofrm a topological search


for each vertex we have aiscover ytiem and a finish time
IF there is no cycle in this directed graph then we can output a topographical sort.


