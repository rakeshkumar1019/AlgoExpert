Question Link: https://leetcode.com/problems/binary-tree-inorder-traversal/

Complexity:
- Time: O(n)
- Space : O(h)

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
    void inOrderHelper(TreeNode* root, vector<int> &res){
        if(root==nullptr) return;
        stack<TreeNode*>s;
        s.push(root);
        while(!s.empty()){
            TreeNode* currNode=s.top();
            if(currNode->left){
                s.push(currNode->left);
                currNode->left=nullptr;
            }else{
                res.push_back(currNode->val);
                s.pop();
                if(currNode->right){
                    s.push(currNode->right);
                }
            }
        }
    }
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> res;
        if(root==nullptr) return res;
        inOrderHelper(root,res);
        return res;
    }
};
```
