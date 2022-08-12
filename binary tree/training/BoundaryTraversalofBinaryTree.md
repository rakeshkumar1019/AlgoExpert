Question Link : https://practice.geeksforgeeks.org/problems/boundary-traversal-of-binary-tree/1

```cpp
class Solution {
private:
    void leftNodes(Node* root,vector<int> &res){
        if(root==nullptr) return;
        if(root->left==nullptr && root->right==nullptr) return;
        res.push_back(root->data);
        if(root->left){
            leftNodes(root->left,res);
        }else{
            leftNodes(root->right,res);
        }
    }
    //pre order Traversal
    void leafNodes(Node *root,vector<int> &res){
        if(root==nullptr) return;
        if(root->left==nullptr && root->right==nullptr){
            res.push_back(root->data);
        }
        leafNodes(root->left,res);
        leafNodes(root->right,res);
    }
    
    void rightNodes(Node* root,vector<int> &res){
        if(root==nullptr) return;
        if(root->left == nullptr && root->right==nullptr) return;
        if(root->right){
            rightNodes(root->right,res);
        }else{
            rightNodes(root->left,res);
        }
        res.push_back(root->data);
    }
public:
    vector <int> boundary(Node *root)
    {
        vector<int> res;
        if(root==nullptr) return res;
        res.push_back(root->data);
        //left Node
        leftNodes(root->left,res);
        //leafs Nodes of Left subtree
        leafNodes(root->left,res);
        //leafs nodes of right Subtree
        leafNodes(root->right,res);
        //reverse right nodes
        rightNodes(root->right,res);
        return res;
    }
};
```
