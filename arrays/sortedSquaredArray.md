# Sorted Squared Array
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/sortedSquareArray.png)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/sortedSquareArray.png)

#### Brute Force Approch :  Square the Number & Sort
Complexity:
- Time: O(nlogn)
- Space: O(1)

#### Optimal Approch  : Using Two Pointers 
Complexity:
- Time: O(n)
- Space: O(1)

```cpp
#include <vector>
using namespace std;

vector<int> sortedSquaredArray(vector<int> array) {
  int n=array.size();
  vector<int> res(n,0);
  if(n<=0) return res;
  int index=n-1;
  int left=0;
  int right=n-1;
  while(left!=right){
    int leftElement=abs(array[left]);
    int rightElement=abs(array[right]);
    if(leftElement>rightElement){
         res[index]=leftElement*leftElement;
         index--;
         left++;
    }
    if(rightElement>leftElement){
      res[index]=rightElement*rightElement;
      index--;
      right--;
    }
    if(leftElement==rightElement){
      res[index]=leftElement*leftElement;
      index--;
      left++;
      if(left!=right){
        res[index]=rightElement*rightElement;
        index--;
        right--;
      }
    }
  }
  res[index]=array[right]*array[right];
  return res;
}

```
### Note: Can occur **Segmentation Fault** Error
:pushpin: `case: (leftElement==rightElement)`:

`case: [0,0,0,0,0,0]`:negative_squared_cross_mark:

`case: [0,0,0,0,0]`:white_check_mark:
```cpp
 if(leftElement==rightElement){
	 res[index]=leftElement*leftElement;
	 index--;
	 left++;
	 if(left!=right){
		 res[index]=rightElement*rightElement;
		 index--;
		 right--;
	 }
 }
```
