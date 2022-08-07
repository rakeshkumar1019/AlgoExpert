### Complexity:
- Time : O(n)
- Space: O(n) no of leaf nodes is approxmetely half of the tree nodes. O(n/2) = O(n)

```cpp
using namespace std;

// This is the class of the input root. Do not edit it.
class BinaryTree {
public:
  int value;
  BinaryTree *left;
  BinaryTree *right;

  BinaryTree(int value) {
    this->value = value;
    left = nullptr;
    right = nullptr;
  }
};
void branchSumHelper(BinaryTree * root,int total,vector<int> &res){
  total+=root->value;
  if(root->left==nullptr && root->right==nullptr){
    res.push_back(total);
    return;
  }else{
    if(root->left){
      branchSumHelper(root->left,total,res);
    }
    if(root->right){
      branchSumHelper(root->right,total,res);
    }
  }
}

vector<int> branchSums(BinaryTree *root) {
  vector<int> res;
  if(root==nullptr) return res;
  int total=0;
  branchSumHelper(root,total,res);
  return res; 
}

```
