# Merge Overlapping Intervals
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/MergeOverLappingIntervals.png?token=GHSAT0AAAAAABVRPMTD3NLTK5B3WIRL6APOYW5IFEQ)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/MergeOverLappingIntervals.png?token=GHSAT0AAAAAABVRPMTD3NLTK5B3WIRL6APOYW5IFEQ)
Complexity:
- Time : O(n)
- Space : O(n)

>Note: 
>
>Sort the array based on `array[i][0]`
>
>`array[i][1] > array[i-1][0]`

```cpp
#include <vector>
using namespace std;

vector<vector<int>> mergeOverlappingIntervals(vector<vector<int>> intervals) {
  int n=intervals.size();
  vector<vector<int>> res;
  if(n==0) return res;
  sort(intervals.begin(),intervals.end());
  res.push_back(intervals[0]);
  if(intervals[0].size()==1) return res;
  int resInd=0;
  for(int i=1;i<n;i++){
    vector<int>temp;
    if(intervals[i][0]>res[resInd][1]){
      temp.push_back(intervals[i][0]);
      temp.push_back(intervals[i][1]);
      res.push_back(temp);
      resInd++;
    }else{
      res[resInd][1]=max(res[resInd][1],intervals[i][1]);
    }
  }
  return res;
}

```
