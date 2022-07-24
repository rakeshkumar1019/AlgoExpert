# Insertion Sort
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/InsertionSort.png?token=GHSAT0AAAAAABVRPMTDUTTSFJEJ2UECTIFCYW5LNPA)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/InsertionSort.png?token=GHSAT0AAAAAABVRPMTDUTTSFJEJ2UECTIFCYW5LNPA)

#### Complexity:

>Best: O(n) time | O(1) space - where n is the length of the input array
>
>Average: O(n^2) time | O(1) space - where n is the length of the input array
>
>Worst: O(n^2) time | O(1) space - where n is the length of the input array

#### Hint: 

>Divide the input array into two subarrays in place. The first subarray should be sorted at all times and should start with a length of 1, while the second subarray should be unsorted. Iterate through the unsorted subarray, inserting all of its elements into the sorted subarray in the correct position by swapping them into place. Eventually, the entire array will be sorted.


```cpp
#include <vector>
using namespace std;

vector<int> insertionSort(vector<int> array) {
  int n= array.size();
  vector<int> res=array;
  if(n<=1) return res;
  for(int i=1;i<n;i++){
    for(int j=i;j>=1;j--){
      if(res[j]<res[j-1]){
        swap(res[j],res[j-1]);
      }
    }
  }
  return res;
}

```
