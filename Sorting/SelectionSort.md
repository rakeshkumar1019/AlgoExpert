# Selection Sort
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/SelectionSort.png?token=GHSAT0AAAAAABVRPMTDMDOMZ45W246H5PAIYW5MFAA)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/SelectionSort.png?token=GHSAT0AAAAAABVRPMTDMDOMZ45W246H5PAIYW5MFAA)

#### Complexity:
>Best: O(n^2) time | O(1) space - where n is the length of the input array
Average: O(n^2) time | O(1) space - where n is the length of the input array
Worst: O(n^2) time | O(1) space - where n is the length of the input array

#### Hint:
>Divide the input array into two subarrays in place. The first subarray should be sorted at all times and should start with a length of 0, while the second subarray should be unsorted. Find the smallest (or largest) element in the unsorted subarray and insert it into the sorted subarray with a swap. Repeat this process of finding the smallest (or largest) element in the unsorted subarray and inserting it in its correct position in the sorted subarray with a swap until the entire array is sorted.


```cpp
#include <vector>
using namespace std;

vector<int> selectionSort(vector<int> array) {
  int n=array.size();
  vector<int> res=array;
  for(int i=0;i<n-1;i++){
    int minIdx=i;
    for(int j=i+1;j<n;j++){
      if(res[minIdx]>res[j]){
        minIdx=j;
      }
    }
    swap(res[i],res[minIdx]);
  }
  return res;
}

```
