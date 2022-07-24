# Longest Peak
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/LongestPeak.png?token=GHSAT0AAAAAABVRPMTDDL6ICUWEBRSS3GF6YW46JWA)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/LongestPeak.png?token=GHSAT0AAAAAABVRPMTDDL6ICUWEBRSS3GF6YW46JWA)

#### Brute Force Approch:
Complexity:
- Time : O(n)
- Space : O(n)

>Note: 
>1. find all peak
>2. find length of each peak
>3. return max peak length

```cpp
using namespace std;

int findPeakLength(vector<int> array,int peak){
  int n=array.size();
  int leftIndexPeak=peak-2;
  int rightIndexPeak=peak+2;
  while(leftIndexPeak >= 0 && array[leftIndexPeak]<array[leftIndexPeak+1]){
    leftIndexPeak--;
  }
  while(rightIndexPeak <=n-1 && array[rightIndexPeak]<array[rightIndexPeak-1]){
    rightIndexPeak++;
  }
  return rightIndexPeak-leftIndexPeak-1;
}
int longestPeak(vector<int> array) {
  int n=array.size();
  if(n<=2) return 0;
  vector<int> peaks;
  for(int i=1;i<n-1;i++){
    if(array[i]>array[i-1] && array[i]>array[i+1]){
      peaks.push_back(i);
    }
  }

  int m=peaks.size();
  int maxPeakLength=0;
  for(int i=0;i<m;i++){
    int currentPeakLength=findPeakLength(array,peaks[i]);
    maxPeakLength=max(maxPeakLength,currentPeakLength);
  }
  return maxPeakLength;
}

```
# Optimal Approch:
Complexity:
- Time : O(n)
- Space : O(1)

>Note:

>As you iterate through the array from left to right, whenever you find a tip of a peak, expand outwards from the tip until you no longer have a peak. Given what peaks look like and how many peaks can therefore fit in an array, realize that this process results in a linear-time algorithm. Make sure to keep track of the longest peak you find as you iterate through the array.


```cpp
using namespace std;

int longestPeak(vector<int> array) {
  int n=array.size();
  if(n<=2) return 0;
  int idx=1;
  int maxPeakLength=0;
  while(idx<=n-2){
    if(array[idx]>array[idx-1] && array[idx]>array[idx+1]){
      int peak=idx;
      int leftIndexPeak=peak-2;
      int rightIndexPeak=peak+2;
      while(leftIndexPeak >=0 && array[leftIndexPeak] < array[leftIndexPeak+1]){
        leftIndexPeak--;
      }
      while(rightIndexPeak <= n-1 && array[rightIndexPeak] < array[rightIndexPeak-1]){
        rightIndexPeak++;
      }
      int currentLengthPeak=rightIndexPeak-leftIndexPeak-1;
      maxPeakLength=max(maxPeakLength,currentLengthPeak);
      idx=rightIndexPeak;
    }else{
      idx++;
    }
  }
  return maxPeakLength;
}

```

