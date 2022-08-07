##### Diameter is no of Edges b/w root and leaf node
###### Not no of nodes
### Complexity:
- Time: O(n^2)
- Space : O(n) stack

```cpp
using namespace std;

// This is an input class. Do not edit.
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
int height(BinaryTree* tree){
  if(tree==nullptr){
    return 0;
  }
  int leftSubtree=height(tree->left);
  int rightSubtree=height(tree->right);
  return 1+max(leftSubtree,rightSubtree);
}
int getBinaryTreeDiameterHelper(BinaryTree *tree){
   if(tree==nullptr){
      return 0;
    }
    int opt1=getBinaryTreeDiameterHelper(tree->left);
    int opt2=getBinaryTreeDiameterHelper(tree->right);
    int opt3= height(tree->left)+height(tree->right)+1;
    int diameter=max(opt1,max(opt2,opt3));
    return diameter;
}
//O(n^2)
int binaryTreeDiameter(BinaryTree *tree) {
   if(tree==nullptr) return 0;
  // diameter here is not Number of NODES but no of EDGES so Node-1
   return getBinaryTreeDiameterHelper(tree)-1;
}

```

### Complexity:
- Time: O(n)
- Space : O(n) stack

```cpp
using namespace std;

// This is an input class. Do not edit.
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
pair<int,int> getBinaryTreeDiameter(BinaryTree *tree){
  if(tree==nullptr){
    //<diameter,height>
    pair<int,int>p ={0,0};
    return p;
  }
  pair<int,int>left=getBinaryTreeDiameter(tree->left);
  pair<int,int>right=getBinaryTreeDiameter(tree->right);
  int opt1=left.first;
  int opt2=right.first;
  int opt3=1+left.second+right.second;

  pair<int,int> ans;
  ans.first=max(opt1,max(opt2,opt3));
  ans.second=1+max(left.second,right.second);
  return ans;
  
}
int binaryTreeDiameter(BinaryTree *tree) {
  if(tree==nullptr) return 0;
  return getBinaryTreeDiameter(tree).first-1;
}

```
