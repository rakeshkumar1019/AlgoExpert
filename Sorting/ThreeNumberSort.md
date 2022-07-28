```cpp
#include <vector>
using namespace std;

vector<int> threeNumberSort(vector<int> array, vector<int> order) {
 int n=array.size();
 int left=0;
 int mid=0;
 int right=n-1;
 while(mid<=right){
   if(array[mid]==order[0]){
     swap(array[mid],array[left]);
     left++;
     mid++;
   }else if(array[mid]==order[2]){
     swap(array[mid],array[right]);
     right--;
   }
   else mid++;
 }
 return array;
}

```
