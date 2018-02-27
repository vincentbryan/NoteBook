> Given a binary tree, return all root-to-leaf paths.

For example, given the following binary tree:

```
   1
 /   \
2     3
 \
  5

```

All root-to-leaf paths are:

```
["1->2->5", "1->3"]
```



```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<string> res;
    vector<string> binaryTreePaths(TreeNode* root) {
        if(root != NULL)
            traverse(root, to_string(root->val));
        return res;
    }
    
    void traverse(TreeNode* root, string s){
        if(root != NULL){
            
            if(root->left == NULL && root->right == NULL) res.push_back(s);
            
            if(root->left != NULL) traverse(root->left, s + "->" + to_string(root->left->val));
            if(root->right != NULL) traverse(root->right, s + "->" + to_string(root->right->val));
            
            return;
        }
    }
};
```

