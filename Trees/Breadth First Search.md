***Breadth-First Search***

- - - 

**→ *prioritises breadth - visit all the nodes on one level before moving onto the next level***

- - - 

***Algorithm***

- *generally - BFS is implemented **iteratively***
- *BFS uses a queue data structure → **deque** (double ended queue) - **allowing removal of elements from both the head & tail in O(1)***

```c++
void bfs(TreeNode* root) {
    queue<TreeNode*> queue;

    if (root) {
        queue.push(root);
    }
    
    int level = 0;
    while (queue.size() > 0) {
        cout << "level: " << level << endl;
        int length = queue.size();
        for (int i = 0; i < length; i++) {
            TreeNode* curr = queue.front();
            queue.pop();
            cout << curr->val_ << ' ';
            if (curr->left) {
                queue.push(curr->left);
            }
            if (curr->right) {
                queue.push(curr->right);
            }
        }
        level++;
        cout << endl;
    }
}
```

- *append root onto the queue and loop through the queue such that at any given time - the queue only holds the nodes on a certain level*
- *ensures that the levels are visited in order and that we do not mix up the levels*

- *as long as the queue is not empty - code removes the nodes that are present in the queue and add its children to the queue*
- *therefore when we remove root - 4 - we add its children - 3 and 6 - to the queue*
- *then we remove 3 - and add its child 2*
- *then we remove 6 - and add its children 5 and 7*
- *due to the FIFO nature of the queue - we ensure that we visit the nodes from left to right*
- *the queue becomes empty when we have visited all of the nodes*

- - - 

***Complexity***

- *total work done = c x n, where n is the number of nodes in the tree, and c is the amount of work done to each node (printing the node, appending the node, and removing it)*
- ***Time Complexity*** → $O(n)$

<br>

- ***Space Complexity*** → $O(b)$
- *b - maximum breadth of the tree (max. number of tree nodes at any level)*
- *for a balanced tree = last level →* $O(2^h)$

- - -
