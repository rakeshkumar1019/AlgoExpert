
## Recursive Approch

### Complexity
- Time: O(n)
-  Space : O(h) h is height of tree
```cpp
#include <vector>
using namespace std;

class BinaryTree {
public:
  int value;
  BinaryTree *left;
  BinaryTree *right;

  BinaryTree(int value);
  void insert(vector<int> values, int i = 0);
  void invertedInsert(vector<int> values, int i = 0);
};

void invertBinaryTree(BinaryTree *tree) {
    if(tree==nullptr) return;
     if(tree->left == nullptr && tree->right == nullptr){
       return;
     }
     swap(tree->left,tree->right);
     invertBinaryTree(tree->left);
     invertBinaryTree(tree->right);
}

```
# Itrative Approch
### Complexity
- Time: O(n)
-  Space : O(h) stack

```cpp
#include <vector>
#include <stack>
#include <bits/stdc++.h>
using namespace std;

class BinaryTree {
public:
  int value;
  BinaryTree *left;
  BinaryTree *right;

  BinaryTree(int value);
  void insert(vector<int> values, int i = 0);
  void invertedInsert(vector<int> values, int i = 0);
};

void invertBinaryTree(BinaryTree *tree) {
  if(tree == nullptr) return;
  stack<BinaryTree* > storeTreeLevel;
  storeTreeLevel.push(tree);
  while(!storeTreeLevel.empty()){
    BinaryTree* currNode=storeTreeLevel.top();
    storeTreeLevel.pop();
    if(currNode == nullptr){
      continue;
    }
    swap(currNode->left,currNode->right);
    storeTreeLevel.push(currNode->left);
    storeTreeLevel.push(currNode->right);
  }
}

```
