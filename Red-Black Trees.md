So recall the binary search tree property:
- Let x be a node in a binary search tree
	1. If y is in left subtree of x, then $key[y]\leq key[x]$
	2. If y is in right subtree of x, then $key[y]\geq key[x]$
remember that operations on a binary search tree typically take around O(h) where h is the height of the tree. Binary Search Trees running time: O(h), h=height of tree, if a tree is balanced then the O deters to O(lg(n))
## Red-Black Tree 
Binary search tree with an extra one-bit color field in each node, red or black.
This color value constrains the way the nodes can be colored on any path from the root to a leaf. This property ensures that the tree is balanced. 
Red-Black trees must satisfy the binary search tree property as well as their own unique properties. 
- every node is either red or black.
- the root is black 
- all the leaves are black
- if a node is red then both of its children are black, no two consequence red nodes on a simple path from the node to a leaf
- For each node all the simple paths from that node to descendant leaves contain the same number of black nodes. 
Height of a node x: h(x) is the number of edges in the longest path to a lead 
Black-Height of a node x: bh(x) is the number of black nodes ( including NIL) on the path from x to a leaf, not counting x
- Due to the unique properties of the red black tree the black-height is guaranteed to be unique
***Most Important Property*** 
A red-black tree with n keys has height $h \leq 2lg(n+1)$ 
To prove this, we need to prove two other claims first: 
1. Any node x with height h(x) has $bh(x) \leq \frac{h(x)}{2}$ 
2. the subtree rooted at any node x contains at least $2^{bh(x)-1}$ internal nodes 
Okay, so let's prove any node x with height h(x) has bh(x)h(x)/2 
*Proof*:
Recall, the property, no two consecutive red nodes on a simple path from the root to a leaf
- at most h/2 red nodes on the path from the node to a leaf
- Hence at least h/2 are black 
So now let's prove that the subtree rooted at any node x contains at least $2^{bh(x)-1}$ internal nodes.
1. *Basis*: h[x]=0
	- x is a leaf node( NIL[T]) -> bh(x)=0
	- Number of internal nodes $2^0 -1 =0$ 
2. Inductive Hypothesis: assume it is true for h[x] = h-1
	-  Prove that it is true for h[x]=h
	- Let bh(x)=b, then any child y of x has:
		- bh(y) =b( if the child is red), or
		- bh(y) b-1( if the child is black) 
