# Three Number Sum
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/threeNumberSum.png?token=GHSAT0AAAAAABVRPMTD67WXL4BA5MLQSNTOYWXXUWA)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/threeNumberSum.png?token=GHSAT0AAAAAABVRPMTD67WXL4BA5MLQSNTOYWXXUWA)
#### Brute Force Approch: Using 3 Loops
Complexity:
- Time: O(n^3)
- Space: O(1)

#### Optimal Approch: Using Sort & Two Pointers 
Complexity:
- Time: O(n^2 + nlogn)
- Space: O(1)

## INTUITION:
- Sort the array
- loop from index: 0 to n-2
- currentNumber=array[index]
- use two pointers left = index +1 , right = n-1
- triplet=currentNumber+ array[left] + array[right]
`while(left<right)`
1 .If (triplet== targetSum)
	- Push in result array & do left++ , right--
	> 	 why  left++ , right-- ?
	> 	 if we just do left++ , triplet > targetSum
	> 	if we just fo right--, triplet < targetSum
	> 	so we are  doing both

2 . Else if(triplet < targetSum )
-    left++

3 . Else
   - right--
   
```cpp
#include <vector>
using namespace std;

vector<vector<int>> threeNumberSum(vector<int> array, int targetSum) {
 vector<vector<int>> res;
  int n=array.size();
  if(n<3) return res;
  sort(array.begin(),array.end());
  for(int i=0;i<n-2;i++){
     int cN=array[i];
     int left=i+1;
     int right=n-1;
     while(left<right){
       int currentTotal=cN+array[left]+array[right];
       if(currentTotal==targetSum){
           vector<int> triplet;
           triplet.push_back(cN);
           triplet.push_back(array[left]);
           triplet.push_back(array[right]);
           res.push_back(triplet);
           left++;
           right--; 
       }else if(currentTotal < targetSum){
            left++;
       }else{
         right--;
       }
     }
  }
  return res;
}

```
