T.C: O(n)

S.C: O(1)

```cpp

#include <vector>
using namespace std;

int kadanesAlgorithm(vector<int> array) {
  if(array.size()<=0) return 0;
  int maxVal=array[0];
  int maxSoFar=array[0];
  for(int i=1;i<array.size();i++){
    maxSoFar=max(array[i],maxSoFar+array[i]);
    maxVal=max(maxVal,maxSoFar);
  }
  return maxVal;
}

```
