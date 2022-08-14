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
};

int maxPathSumHelper(BinaryTree* tree,int &maxSum){
  if(tree == nullptr) return 0;
  int leftSubTree=max(maxPathSumHelper(tree->left,maxSum),0);
  int rightSubTree=max(maxPathSumHelper(tree->right,maxSum),0);
  int opt1=max(max(leftSubTree,rightSubTree)+tree->value,tree->value);
  int opt2=max(opt1,leftSubTree+rightSubTree+tree->value);
  maxSum=max(maxSum,opt2);
  return opt1;
  
}
int maxPathSum(BinaryTree tree) {
  int maxSum=INT_MIN;
  maxPathSumHelper(&tree,maxSum);
  return maxSum;
}

```
