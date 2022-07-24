# Bubble Sort
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/BubbleSort.png?token=GHSAT0AAAAAABVRPMTDKNK4B2ASQ7E4YPNCYW5KMNQ)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/BubbleSort.png?token=GHSAT0AAAAAABVRPMTDKNK4B2ASQ7E4YPNCYW5KMNQ)

#### Complexity:
>Best: O(n) time | O(1) space - where n is the length of the input array
>
>Average: O(n^2) time | O(1) space - where n is the length of the input array
>
>Worst: O(n^2) time | O(1) space - where n is the length of the input array

####  Note: If Inner loop is sorted the outer loop is also sorted
```cpp
#include <vector>
using namespace std;

vector<int> bubbleSort(vector<int> array) {
   int n=array.size();
   vector<int> res=array;
   bool isSwap;
   for(int i=0;i<n-1;i++){
     isSwap=false;
     for(int j=0;j<n-i-1;j++){
       if(res[j]> res[j+1]){
         swap(res[j],res[j+1]);
         isSwap=true;
       }
     }
     //if the inner loop is sorted then the outer loop is also sorted
     if(!isSwap) break;
   }
  return res;
}

```
