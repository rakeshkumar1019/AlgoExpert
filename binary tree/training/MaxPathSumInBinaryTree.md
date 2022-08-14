Question Link: https://leetcode.com/problems/binary-tree-maximum-path-sum/

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    int res=INT_MIN;

     int maxPathHelper(TreeNode* root){
        if(root == NULL){
            return 0;
        }
        int left=maxPathHelper(root->left);
        int right=maxPathHelper(root->right);
        int opt1=max(max(left,right)+root->val,root->val);
        //left+right+root  or opt1
        int opt2=max(opt1,left+right+root->val);
        res=max(res,opt2);
        return opt1;
    }
      int maxPathSum(TreeNode* root) {
       maxPathHelper(root);
       return res;
    }
};
```
