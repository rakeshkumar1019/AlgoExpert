T.C: O(logn)

S.C : O(1)

```cpp
#include <vector>
using namespace std;

int indexEqualsValue(vector<int> array) {
  int n=array.size();
  int left=0;
  int right=n-1;
  while(left<=right){
    int index=left+(right-left)/2;
    int value=array[index];
    if( index > value){
      left=index+1;
    }else if (index == value && index-1 != array[index-1]){
      return index;
    }else if( index == value && index-1 == array[index-1]){
      right=index-1;
    }else if( index < value){
      right=index-1;
    }
  }
  return -1;
}

```
