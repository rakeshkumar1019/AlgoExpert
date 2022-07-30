# Permutations 
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/Permutation.png)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/Permutation.png)

##### Complexity:
- Time: O(n*n!)
- Space: O(n)

```cpp
#include <vector>
using namespace std;
void getPermutationsHelper(vector<int> &array,int idx,vector<vector<int>> &res){
  if(idx==array.size()-1){
    res.push_back(array);
    return;
  }
  for(int i=idx;i<array.size();i++){
    swap(array[i],array[idx]);
    getPermutationsHelper(array,idx+1,res);
    swap(array[i],array[idx]);
  }
  return;
}
vector<vector<int>> getPermutations(vector<int> array) {
  vector<vector<int>> res;
  if(array.size()==0) return res;
  getPermutationsHelper(array,0,res);
  return res;
}

```
