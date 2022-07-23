# Move Element To End
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/moveElementToEnd.png?token=GHSAT0AAAAAABVRPMTDMJUMKL3GL6VA73EQYW33NEQ)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/moveElementToEnd.png?token=GHSAT0AAAAAABVRPMTDMJUMKL3GL6VA73EQYW33NEQ)

####  In Place Approch: Using Two Pointers
Complexity:
- Time:O(n)
- Space:O(1)

```cpp
#include <vector>
using namespace std;
vector<int> moveElementToEnd(vector<int> array, int toMove) {
 int n=array.size();
 int left=0;
 int right=n-1;
 while(left<right){
   if(array[right]==toMove){
     right--;
   }else if(array[left]==toMove){
     swap(array[left],array[right]);
     left++;
     right--;
   }else{
     left++;
   }
 }
return array;
}
```
