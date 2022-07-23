# Smallest Difference
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/SmallestDifference.png?token=GHSAT0AAAAAABVRPMTCO75R5PJUJES2SR6WYW32OQQ)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/SmallestDifference.png?token=GHSAT0AAAAAABVRPMTCO75R5PJUJES2SR6WYW32OQQ)
#### Brute Force: Using Two Loops
Complexity:
- Time : O(n^2)
- Space : O(1)

```cpp
#include <vector>
using namespace std;
vector<int> smallestDifference(vector<int> arrayOne, vector<int> arrayTwo) {
  int n= arrayOne.size();
  int m= arrayTwo.size();
  int minDiff=INT_MAX;
  vector<int> res={0,0};
  for(int i=0;i<n;i++){
    for(int j=0;j<m;j++){
      if(abs(arrayOne[i]-arrayTwo[j])<minDiff){
        minDiff=abs(arrayOne[i]-arrayTwo[j]);
        res[0]=arrayOne[i];
        res[1]=arrayTwo[j];
      }
    }
  }
  return res;
}
```
#### Optimal Approch: Using Two Pointers
Complexity:
- Time : O(nlogn + mlogm)
- Space : O(1)

> ## Hint:  Two Pointers
> 
> Same Number - Same Number == 0
> 
> Small Number - Big Number : Increase Left Number
> 
> Big Number - Small Number : Increase Right Number

```cpp
#include <vector>
using namespace std;
vector<int> smallestDifference(vector<int> arrayOne, vector<int> arrayTwo) {
  int n=arrayOne.size();
  int m=arrayTwo.size();
  sort(arrayOne.begin(),arrayOne.end());
  sort(arrayTwo.begin(),arrayTwo.end());
  int left=0;
  int right=0;
  vector<int> res={0,0};
  int minDiff=INT_MAX;
  while(left<n && right< m){
    int currentDiff=abs(arrayOne[left]-arrayTwo[right]);
    if(currentDiff < minDiff){
      minDiff=currentDiff;
      res[0]=arrayOne[left];
      res[1]=arrayTwo[right];
    }
    if(arrayOne[left]<arrayTwo[right]){
      left++;
    }else{
      right++;
    }
  }
  return res;
}

```

