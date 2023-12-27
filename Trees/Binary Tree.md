***Binary Tree***

- - - 

 → ***data structure with nodes and pointers***

***Nodes***
- → *have at most two pointers (left child & right child pointers)*
- → *first node in a binary tree = root node*
- *→ value of a node can be any data type*

***Leaf Node***
- → *node with no children*

- - - 

***TreeNode Class***

```c++
class TreeNode {
    public:
        int val_;
        TreeNode* left = nullptr;
        TreeNode* right = nullptr;

        TreeNode(int val) {
            val_ = val;
        }
};
```

- *binary tree pointers can only point in one direction → **cycles are not allowed in binary trees***
- *a binary tree is an **undirected graph with no cycles** → leaf node guaranteed to exist*

- *the same applies to the decision trees that are used in recursion*

- - - 

***Properties***

***Root Node***
- *→ highest node in the tree that has no parent node, all of the nodes in the tree can be reached by the root node*

***Leaf Node***
- *→ nodes with no children - nodes at the last level of the tree are guaranteed to be lead nodes*

***Height***
- *→ height of a binary tree measured from the root node to the lowest leag node*
- *→ height of a single node = 1 (if counting the node itself) - or 0 (if not)*
- *→ sometimes the height is counted by the number of edges that are in between the nodes instead of the nodes themselves (height of tree = n-1 = number of edges)*

***Depth***
- *→ depth of a binary tree node - measured from itself up to the root*

***Ancestor***
- → *a node connected to all of the nodes below it - considered an ancestor to those nodes*

***Descendent***
- → *a descendent of a node is either child of the node or some other descendent of the node*

- - - 
