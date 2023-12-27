
- - - 

***Binary Search Tree***

- - - 

***→ variation of binary trees with a sorted property***

***BST Sorted Property:***
- → *every left child must be smaller than its parent and every right child must be greater than its parent*
- *→ BSTs do not allow duplicates*

- *BST property applied to subtrees to → while a node which has a value smaller than the root will be on the left subtree - important to determine where exactly in the left subtree the value will be inserted*

- - - 

***Motivation***

- *with BSTs → can search values in $O(logn)$ time - while also running insertion/deletion in $O(logn)$ time (this takes $O(n)$ time with an array)*
- *so while BSTs don’t offer benefit over sorted arrays for search functionality - they are better for insertion/deletion*

- - - 

***BST Search***

- *trees are best traversed through recursion (could do iteratively - but would require maintaining a stack)*
- *take this BST & target 3*

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/9c42ae26-33f4-4110-e49b-509c7dae3600/sharpen=1)

- *start by comparing the root value against the target*
- *2 is too small - so our target must be on the right - meaning we can eliminate the left subtree*
- *when we go right - the first node is 3 - which equals target - so we return true from that recursive call, meaning our target does exist in the tree*

```c++
bool search(TreeNode* root, int target) {
    if (!root) {
        return false;
    }

    if (target > root->val_) {
        return search(root->right, target);
    } else if (target < root->val_) {
        return search(root->left, target);
    } else {
        return true;
    }
}
```

- - -

***Complexity (BST Search)***

***Time Complexity:***
- ***balanced binary tree → search algorithm: $O(logn)$**
- *balanced → height of the left subtree = height of the right subtree (or a difference of 1)*
- *in a balanced tree we eliminate half of the nodes each time → $O(logn)$*

- *in a skewed binary tree → time complexity $O(n)$ (worst case)*

<br>

***Space Complexity:***
- $O(h)$
- *h → height of the tree (maximum amount of space used to store the call stack during the deepest recursive search)*

- - - 

