***Depth First Search***

- - - 

***→ way of traversing binary search trees that prioritises depth rather than breadth***

- - - 

***Algorithm***

- *keep traversing down the left subtree or the right subtree until there are no more nodes left*
- *various methods: inorder, preorder, postorder → visit the root, left child, and right child in different orders*
- *DFS → **best implemented using recursion***

- - - 

***Inorder Traversal***

- ***visiting the left child first - then the parent node - then the right child***
- *returns the nodes visited in sorted order*

```c++
void inorder(TreeNode* root) {
    if (!root) {
        return;
    }
    inorder(root->left);
    cout << root->val_ << endl;
    inorder(root->right);
}
```

- *if we prioritised right before left - we would return the nodes in reverse order*

- *the reason the nodes will print in a sorted order is because of the BST property
- *since we know all values to the left of a node are smaller - this means we won't hit our base case until we reach the left-most node which is also the smallest node*
- *after visiting this - we will traverse up - visit the parent and then visit the right-subtree*

![[45c0cwnx.bmp]]

- - - 

***Preorder Traversal***

- ***visits the parent - then left child - then right child***

```c++
void preorder(TreeNode* root) {
    if (!root) {
        return;
    }
    cout << root->val_ << endl;
    preorder(root->left);
    preorder(root->right);
}
```

![In-order Traversal](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/9388095e-8f09-4725-fc1d-27988a291c00/sharpen=1)

- - - 

***Postorder Traversal***

- ***visits the left child, then the right child, then the parent***

```c++
void postorder(TreeNode* root) {
    if (!root) {
        return;
    }
    postorder(root->left);
    postorder(root->right);
    cout << root->val_ << endl;
}
```

![In-order Traversal](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/1abfa778-c56d-4563-9860-5f58bcee6c00/sharpen=1)

- - - 

***Complexity***

***DFS:***
- *have to visit every node of the tree 0 if there are n nodes*
- ***Time Complexity → O(n)***

- ***Space Complexity*** → $O(h)$
- *(height of recursive call stack - logn for balanced tree & n for skewed tree)*

***Sorting:***
- *can sort an array using a binary tree*
- *first - build the tree and insert each value*
- *n values & inserting into the binary tree → logn time*
- *therefore → building tree is $O(n+nlogn)$*
- *but only consider the highest term*
- *so **sorting array using binary tree** → **$O(nlogn)$ time***
- → $O(n)$ ***space***

- - - 
