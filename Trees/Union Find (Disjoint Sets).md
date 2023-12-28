***Union Find (Disjoint Sets)***

- - - 

***Union Find***

→ ***keeping track of connected components in a graph**
→ ***detecting cycles in a graph***

***Find:*** *determines which set particular element belongs to by finding parent node*
***Union:*** *joins two sets together by taking parents & making one parent of another*

- *this can be achieved with DFS using a hashset*
- *DFS is a good choice when using a static graph (i.e. no edges can be added over time)*

- *Union Find a better choice for **dynamic graphs (adding edges over time)***

- - - 

***Disjoint Sets***

***→ do not have any elements in common***
***→ their intersection is the empty set***

- *Union Find operates on Disjoint Sets*
- *to perform a union of two vertices → ensure those vertices belong to disjoint sets*

- - - 

***Example***

- *given an array of edges*
- *e.g. `edges: [1,2], [4,1], [2,4]
- *each array in edges in an undirected, connected pair of vertices*
- *build a graph of connected components*

- *Union Find → Forest of Trees → Many Trees of Connected Components*
- ***Union: join two sets together*
- ***Find: determine the set which a particular element belongs to - by finding the parent node*

- *initially → each vertex exists by itself*
- *for each vertex, the pointer to it’s parent, points to itself*

![[ppanblsw.bmp]]

- *from the array of edges, want to join the nodes together, to create connected components
- *this can be done by finding the parent of the vertices, and then making the one of the parents the child of the other parent

- *this ensures that the connected vertices are part of the same component
- *the correct graph structure is not maintained, but the connected components are correct*

- *which parent is selected to be the parent/child matters when the two components have different ranks (height)*
- *as we want the components to be as balanced as possible*

- - - 

***Implementation***

```cpp
class UnionFind {
public:
    unordered_map<int, int> par_;
    unordered_map<int, int> rank_;

    UnionFind(int n) {
        for (int i = 1; i <= n; i++) {
            par[i] = i;
            rank[i] = 0;
        }
    }
};
```

- *to implement the Union Find → use a UnionFind class*
- *instantiates a parent & rank HashMap*

- *the parent map stores the parent of each vertex*
- *initially each vertex is its own parent, representing that each element is in its own set*
- *when the two sets are unioned, the parent of one vertex is updated to point to the other parent*

- *the rank map stores the rank (height) of the trees represented by each vertex*

- *the constructor takes an integer n, representing n vertices*
- *the parent of each vertex is set to itself*
- *the rank of each vertex is set to 0*

- - - 

***Union by Rank***

- *the rank is used to keep the tree balanced during the union operation*
- *when the two sets of different ranks are unioned, the set with the smaller rank is attached to the root of the set with the larger rank **(Union by Rank)***
- *if both sets have the same rank, you can attach either set and increment the rank of the resultant set*

- - - 

***Find***

→ ***determine the set which a particular element belongs to - by finding the parent node***

```cpp
// Find the Parent of n, with Path Compression
int find(int n) {
    int p = par[n];
    while (p != par[p]) {
        par[p] = par[par[p]]; // Path Compression
        p = par[p];
    }
    par[n] = p;
    return p;
}
```

- *takes a vertex n & returns its parent*
- *using the parent hashmap, where the key is the vertex & the value is the parent*
- *while the parent is not itself → update the parent to the parent of the parent node (moving up the tree)*

- - - 

***Path Compression:***

- *as we are performing union on a large number of vertices → can result in a long chain*
- *taking a lot of steps to determine the parent*
- *reduce the amount of steps → traversing up two vertices at a time instead of one*
- *when we are going up the tree, the parent is actually the grandparent*
- *flattens the tree somewhat*
- *this does not give any performance improvements for the first iteration, will when finding the parent of that vertex again*
- *this is the iterative approach*

- *there is also full (recursive) path compression, which updates each node to point directly to the root as you go up the tree*

```cpp
int find(int x) {
    if (par_[x] == x)
        return x;
    return par[x] = find(par[x]); // Full Path Compression
}
```

- - - 

***Union***

→ ***joins two sets together by taking parents & making one parent of another***

```cpp
// Union by Rank
// Return False if already connected, true otherwise.
bool union(int n1, int n2) {
    int p1 = find(n1), p2 = find(n2);
    if (p1 == p2) {
        return false;
    }

    if (rank_[p1] > rank_[p2]) {
        par_[p2] = p1;
    } else if (rank_[p1] < rank_[p2]) {
        par_[p1] = p2;
    } else {
        par_[p1] = p2;
        rank_[p2] += 1;
    }
    return true;
}
```

- *takes two vertices and determines if a union can be formed*
- *if two vertices share the same parent → a union cannot be formed and we can return false*
- *if they are of different rank → the parent with the lowest rank becomes the child to the parent with the highest rank*
- *if they are the same rank → choose either (set p2 to be the parent of p1) and increment the rank by 1*

*example:*
![[1u1a6syv.bmp]]

- *when we get to [2,4] → have the same parent → they belong to the same connected component → there is a cycle in the graph*

- - - 

***Complexity***

***Space Complexity: $O(n)$

***Find:***
- *without path compression → **Time Complexity:** $O(n)$*
- *as tree is just like a chain in a linked list in which we have to traverse every single node to find the parent*

- *with path compression → **Time Complexity** $O(logn)$ (since we are updating the parent to be the grandparent each time)*

- *with union by rank → **Time Complexity:*** $O(logn)$

- *with path compression & union by rank → **Time Complexity:*** $\alpha(n)$ → *simplifies to constant time:* $O(1)$

- *Find runs for number of edges* $m$
- → ***Total Time Complexity:*** $O(mlogn)$ 
- → ***Total Time Complexity:*** $O(m)$ *(with path compression & union by rank)

***Union***
-  ***Time Complexity*** $O(1)$

- - - 

