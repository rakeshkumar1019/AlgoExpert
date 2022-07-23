# First Duplicate Value
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/FirstDuplicateValue.png?token=GHSAT0AAAAAABVRPMTDCFLLNM3PACI2AQCSYW4DOYQ)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/FirstDuplicateValue.png?token=GHSAT0AAAAAABVRPMTDCFLLNM3PACI2AQCSYW4DOYQ)

#### Brute Force: Using Map
Complexity:
- Time: O(n)
- Space: O(n)

#### Optimal Approch: Uisng index Manipulation
Note : `1=> N <=n`
Complexity:
- Time: O(n)
- Space: O(1)

```cpp
#include <vector>
using namespace std;

int firstDuplicateValue(vector<int> array) { 
  int n= array.size();
  if(n<=1) return -1;
  for(int i=0;i<n;i++){
    int idx=abs(array[i])-1;
    if(array[idx]<0){
      return idx+1;
    }
    array[idx]=array[idx]* -1;
  }
  return -1; 
}

```

