  Question link: https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/


## Approch:
> We can use a queue just like we used in Level Order Traversal. But in this case, we can also maintain a flag variable which keeps track of alternate level to reverse the order of the corresponding level traversal.flag==true implies we have to insert from left to right and flag==false means we have to insert element from right to left our answer arraylist.
>
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
    vector<vector<int>> zigzagLevelOrder(TreeNode* root) {
        vector<vector<int>> output;
        if(root == nullptr) return output;
        queue<TreeNode*> q;
        q.push(root);
        bool leftToRight=true;
        while(!q.empty()){
            int q_size=q.size();
            vector<int> curr_Level(q_size);
            for(int i=0;i<q_size;i++){
                TreeNode* currNode=q.front();
                q.pop();
                int index= leftToRight ? i : q_size-i-1;
                curr_Level[index]=currNode->val;
                if(currNode->left){
                    q.push(currNode->left);
                }
                if(currNode->right){
                    q.push(currNode->right);
                }
            }
            leftToRight=!leftToRight;
            output.push_back(curr_Level);
        }
        return output;
    }
};
```

### Complexity
- Time Complexity: O(N)
- Auxiliary Space: O(N) for queue data structure
