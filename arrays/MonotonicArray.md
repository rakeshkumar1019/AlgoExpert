# Monotonic Array
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/MonotonicArray.png?token=GHSAT0AAAAAABVRPMTD4MJSJJPQWQJ5U2VWYW34LRQ)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/MonotonicArray.png?token=GHSAT0AAAAAABVRPMTD4MJSJJPQWQJ5U2VWYW34LRQ)
Complexity:
- Time: O(N)
- Space: O(1)

#### Note: Can have same number in arrays `[1,1,1,1,1]`
```cpp
using namespace std;
bool isMonotonic(vector<int> array) {
  int n=array.size();
  if(n<=1) return true;
  int i=0;
  while(i<n){
    if(i+1<n && array[i]==array[i+1]){
      i++;
    }else{
      break;
    }
  }
  if(i==n-1) return true;
  string flag;
  if(array[i]>array[i+1]){
    flag="GREATER";
  }else{
    flag="SMALLER";
  }
  for(;i<n-1;i++){
    if(flag=="GREATER"){
      if(array[i]<array[i+1])return false;
    }else{
      if(array[i]>array[i+1])return false;
    }
  }
  return true;
}

```
