## Power Set

### Recursive Approch

```cpp
#include <vector>
using namespace std;
//recursive solution

void generatePowerSet(vector<int> &array,int index,vector<int> &subset, vector<vector<int>> &subsets){
  if(index==array.size()){
    subsets.push_back(subset);
    return;
  }
  //doesn't include an element in the subset
  generatePowerSet(array,index+1,subset,subsets);
  //include an element in a subset
  subset.push_back(array[index]);
  generatePowerSet(array,index+1,subset,subsets);
  subset.pop_back();
  
}
vector<vector<int>> powerset(vector<int> array) {
  vector<vector<int>> subsets;
  vector<int> subset;
  generatePowerSet(array,0,subset,subsets);
  return subsets;
}

```

### Itrative Approch
```cpp
#include <vector>
using namespace std;
//Non recursive solution
vector<vector<int>> powerset(vector<int> array) {
  vector<vector<int>> subsets;
  vector<int> subset;
  subsets.push_back(subset);
  int n=array.size();
  for(int i=0;i<n;i++){
    int size=subsets.size();
    for(int j=0;j<size;j++){
      vector<int> currentSubset=subsets[j];
      currentSubset.push_back(array[i]);
      subsets.push_back(currentSubset);
    }
  }
  return subsets;
}

```
