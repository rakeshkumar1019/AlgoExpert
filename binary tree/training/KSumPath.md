Question Link: https://practice.geeksforgeeks.org/problems/k-sum-paths/1

Complexity: 
- Time: O(n*h)
- Space : O(h)

```cpp
/*
struct Node 
{
    int data;
    Node *left;
    Node *right;

    Node(int val) {
        data = val;
        left = right = NULL;
    }
};
*/
class Solution{
  private: 
  void sumKHelper(Node* root,int k, int &count,vector<int> res){
      if(root==NULL){
          return;
      }
      res.push_back(root->data);
      sumKHelper(root->left,k,count,res);
      sumKHelper(root->right,k,count,res);
      int size=res.size();
      int currSum=0;
      for(int i=size-1;i>=0;i--){
          currSum+=res[i];
          if(currSum==k){
             count++; 
          }
      }
  }
  public:
    int sumK(Node *root,int k)
    {
        if(root==nullptr) return 0;
        vector<int> res;
        int count=0;
        sumKHelper(root,k,count,res);
        return count;
    }
};
```
