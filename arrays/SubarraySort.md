# Subarray Sort
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/SubarraySort.png)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/SubarraySort.png)

#### Brute Force Approch: Using Sorting
Ex : `array=[1,2,3,6,5,4,7]` `output=[3,5]`
After `sorted array=[1,2,3,4,5,6,7]` `misplacedElementIndex=[3,5]`
Complexity:
- Time: O(nlogn)
- Space: O(1)

#### Optimal Approch: Uisng Small & Big Unsorted Number
Complexity:
- Time: O(n)
- Space: O(1)

##### Hint 1:

>Realize that even a single out-of-order number in the input array can call for a large subarray to have to be sorted. This is because, depending on how out-of-place the number is, it might need to be moved very far away from its original position in order to be in its sorted position.

##### Hint 2:
>Find the smallest and largest numbers that are out of order in the input array. You should be able to do this in a single pass through the array.

##### Hint 3:
>Once you've found the smallest and largest out-of-order numbers mentioned in Hint 2, find their final sorted positions in the array. This should give you the extremities of the smallest subarray that needs to be sorted.

```cpp
#include <vector>
using namespace std;
bool isUnsortedNumber(int i,int num,vector<int> array,int n){
  if(i==0){
    return array[i] > array[i+1];
  }
  if(i==n-1){
    return array[i]< array[i-1];
  }
  return array[i] < array[i-1] || array[i] > array[i+1];
}
vector<int> subarraySort(vector<int> array) {
    int n=array.size();
    int small=INT_MAX;
    int big=INT_MIN;
    for(int i=0;i<n;i++){
      int num=array[i];
      if(isUnsortedNumber(i,num,array,n)){
        small=min(small,num);
        big=max(big,num);
      }
    }
    vector<int> res;
    if(small==INT_MAX){
      res.push_back(-1);
      res.push_back(-1);
      return res;
    }
    int smallIdx=0;
    int bigIdx=n-1;
    while(small>=array[smallIdx]) smallIdx++;
    while(big<=array[bigIdx]) bigIdx--;
    res.push_back(smallIdx);
    res.push_back(bigIdx);
    return res;
}

```
