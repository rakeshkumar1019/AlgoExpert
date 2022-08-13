### Complexity:
- Expected Time Complexity:O(N).
- Expected Auxiliary Space:O(Height of Tree).


```cpp
/* A binary tree node

struct Node
{
    int data;
    struct Node* left;
    struct Node* right;
    
    Node(int x){
        data = x;
        left = right = NULL;
    }
};
 */

class Solution
{
    public:
    //Function to return the lowest common ancestor in a Binary Tree.
    Node* lca(Node* root ,int n1 ,int n2 )
    {
       if(root==nullptr) return nullptr;
       if(root->data==n1 || root->data==n2) return root;
       
       Node* leftSubTree=lca(root->left,n1,n2);
       Node* rightSubTree=lca(root->right,n1,n2);
       if(leftSubTree!=nullptr && rightSubTree!=nullptr){
           return root;
       }else if(leftSubTree!=nullptr && rightSubTree==nullptr){
           return leftSubTree;
       }else if(leftSubTree==nullptr && rightSubTree!=nullptr){
           return rightSubTree;
       }else{
           return nullptr;
       }
    }
};
```
