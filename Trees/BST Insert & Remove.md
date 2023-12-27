***BST Insert & Remove***

- - - 

- *main benefit of using BSTs over sorted arrays is that we can perform **insertion & removal** in $O(logn)$ time - assuming that the tree is balanced*

- - - 

***Insertion***

- *if we wish to insert a new node into the BST → **traverse the BST to find the right position & insert this node***

![[sjls53v6.bmp]]

```c++
// Insert a New Node & Return the Root of the Tree
TreeNode* insert(TreeNode* root, int val) {
    if (!root) {
        return new TreeNode(val);
    }

    if (val > root->val_) { 
        root->right = insert(root->right, val);
    } else if (val < root->val_) {
        root->left = insert(root->left, val);
    }
    return root;
}
```

- - - 

***Removal***

- *before removing a node from a BST, consider two cases:*
- *the target node has 0 or 1 children*
- *the target node has 2 children*

*case 1: the target node has 0 or 1 children*

![alt text](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/b8f1af6e-2fe6-4429-8765-abf1b92e7a00/sharpen=1)

- *to delete node 2 - which has no children → the left child pointer of 3 now points to NULL*

- *to delete node 3 - which has 1 child → the left child pointer of the root will now point to 2 instead of 3*

![alt text](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/2fa45c14-0ff4-4fdb-20de-795041eeb800/sharpen=1)

*case 2: the target node has 2 children*

- *to delete a node with two children → replace the node with it’s **in-order successor***

- ***in-order successor:*** *the left-most node in the right subtree of the target node*
- *(the smallest node among the nodes that are greater than the target node)*
- *this will ensure that the resulting tree is still a valid BST*

![alt text](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/7cfb33fa-565b-40d4-3938-399d06e48200/sharpen=1)


```c++
// Return the Minmum Value Node of the BST
TreeNode* minValueNode(TreeNode* root) {
    TreeNode* curr = root;
    while (curr && curr->left) {
        curr = curr->left;
    }
    return curr;
}

// Remove a Node & Return the Root of the Tree
TreeNode* remove(TreeNode* root, int val) {
    if (!root) {
        return new TreeNode(val);
    }

    if (val > root->val_) { 
        root->right = remove(root->right, val);
    } else if (val < root->val_) {
        root->left = remove(root->left, val);
    } else {
        if (!root->left) {
            return root->right;
        } else if (!root->right) {
            return root->left;
        } else {
            TreeNode* minNode = minValueNode(root->right);
            root->val_ = minNode->val_;
            root->right = remove(root->right, minNode->val_);
        }
    }
    return root;
}
```

- - - 

***Complexity (Insertion & Deletion)***

- *if the tree given is a balanced binary tree → height will be $log(n)$*
- ***Time Complexity: $O(log(n))$***

- *in worst case - tree is left skewed or right skewed → time complexity $O(n)$

<br>

- ***Space Complexity: $O(h)$***
- → *h: height of tree (maximum recursive stack size in the worst-case)*
- → $O(n)$ *or* $O(logn)$ - *depending on the h*

- - - 
