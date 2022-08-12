## complexity:
- Time: O(n)
- Space: O(h)

```cpp

/*
structure of the node of the binary tree is as
struct Node
{
    int data;
    struct Node *left;
    struct Node *right;

    Node(int x)
    {
        data = x;
        left = NULL;
        right = NULL;
    }
};
*/
class Solution
{
private:
    void  helper(Node* root,int currDepth,int &maxDepth,int currSum,int &maxSum){
        if(root==nullptr) return;
        currSum+=root->data;
        if(root->left==nullptr && root->right==nullptr){
            if(currDepth>maxDepth){
                maxDepth=currDepth;
                maxSum=currSum;
                return;
            }else if(currDepth==maxDepth){
                maxSum=max(currSum,maxSum);
                return;
            }else{
                return;
            }
        }
        helper(root->left,currDepth+1,maxDepth,currSum,maxSum);
        helper(root->right,currDepth+1,maxDepth,currSum,maxSum);
    }
public:
    
    int sumOfLongRootToLeafPath(Node *root)
    {
         if(root==nullptr) return 0;
         int currDepth=0;
         int maxDepth=0;
         int currSum=0;
         int maxSum=INT_MIN;
         helper(root,currDepth,maxDepth,currSum,maxSum);
         return maxSum;
    }
};
```
