#### Complexity:
- Time: O(n^2)
- Space: O(n) stack

```cpp
using namespace std;

// This is an input class. Do not edit.
class BinaryTree {
public:
  int value;
  BinaryTree *left = nullptr;
  BinaryTree *right = nullptr;

  BinaryTree(int value) { this->value = value; }
};

int height(BinaryTree *tree){
  if(tree==nullptr) return 0;
  int leftSubtree=height(tree->left);
  int rightSubtree=height(tree->right);
  return 1+max(leftSubtree,rightSubtree);
}
//O(n^2)
bool heightBalancedBinaryTree(BinaryTree *tree) {
  if(tree==nullptr) return true;
  bool leftSubtree=heightBalancedBinaryTree(tree->left);
  bool rightSubtree=heightBalancedBinaryTree(tree->right);
  bool diffHeight=abs(height(tree->left)-height(tree->right))<=1;
  if(leftSubtree && rightSubtree && diffHeight){
    return true;
  }else{
    return false;
  }
}

```

#### Complexity:
- Time: O(n)
- Space: O(n) stack

```cpp
using namespace std;

// This is an input class. Do not edit.
class BinaryTree {
public:
  int value;
  BinaryTree *left = nullptr;
  BinaryTree *right = nullptr;

  BinaryTree(int value) { this->value = value; }
};
pair<bool,int> isBalancedHelper(BinaryTree *tree){
  if(tree==nullptr){
    // <isBalanced , height>
    pair<bool,int>p=make_pair(true,0);
    return p;
  }
  pair<bool,int> leftSubtree=isBalancedHelper(tree->left);
  pair<bool,int> rightSubtree=isBalancedHelper(tree->right);
  bool left=leftSubtree.first;
  bool right=rightSubtree.first;
  bool diffHeight=abs(leftSubtree.second-rightSubtree.second)<=1;
  pair<bool,int> ans;
  if(left && right && diffHeight){
    ans.first=true;
  }else{
    ans.first=false;
  }
  ans.second=1+max(leftSubtree.second,rightSubtree.second);
  return ans;
}
//O(n)
bool heightBalancedBinaryTree(BinaryTree *tree) {
  if(tree==nullptr) return true;
  return isBalancedHelper(tree).first;
}

```




