# Complexity:
- Time: O(n)
- Space: O(h) where h is height of the tree.


## Recursive Approch
```cpp
using namespace std;

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
int traverse(BinaryTree *root,int depth){
  if(root==nullptr){
    return 0;
  }
  int leftSubTree=traverse(root->left,depth+1);
  int rightSubTree=traverse(root->right,depth+1);
  return depth+leftSubTree+rightSubTree;
  
}
int nodeDepths(BinaryTree *root) {
   if(root==nullptr) return 0;
   int depth=0;
   return traverse(root,depth);
}

```

## Itrative Approch
```cpp
using namespace std;

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

int nodeDepths(BinaryTree *root) {
  if(root==nullptr) return 0;
  int totalDepth=0;
  int currDepth=0;
  queue<BinaryTree*> q;
  q.push(root);
  q.push(nullptr);
  while(!q.empty()){
    BinaryTree *curr=q.front();
    q.pop();
    if(curr==nullptr){
      currDepth++;
      if(!q.empty()){
        q.push(nullptr);
      }
    }else{
      totalDepth+=currDepth;
      if(curr->left!=nullptr){
        q.push(curr->left);
      }
      if(curr->right!=nullptr){
        q.push(curr->right);
      }
    }
  }

  return totalDepth;
}

```
