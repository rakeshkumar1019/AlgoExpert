# Four Number Sum
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/FourNumberSum.png)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/FourNumberSum.png)

#### Brute Force Approch: Using 4 loops
Complexity:
- Time: O(n^4)
- Space: O(n^2)

#### Optimal Approch: Using Map & Pointers
Complexity:
- Time: O(n^2)
- Space: O(n^2)

##### Hint 1:

>You can calculate the sums of every pair of numbers in the array in O(n^2) time using just two for loops. Then, assuming that you've stored all of these sums in a hash table, you can fairly easily find which two sums can be paired to add up to the target sum: the numbers summing up to these two sums constitute candidates for valid quadruplets; you just have to make sure that no number was used to generate both of the two sums.

##### Hint 2: 

>You can do everything described in Hint 1 with just two sibling for loops nested inside a third for loop. Your goal is to create a hash table mapping the sums of every pair of numbers in the array to an array of arrays, with each subarray representing the indices of each pair summing up to that number. Loop through the input array with a simple for loop. Inside this loop, loop through the input array again, starting at the index of the first loop. At each iteration, calculate the difference between the target sum and the sum of the two numbers represented by the indices of the for loops. If that difference is in the hash table that you're building, then valid quadruplets can be formed by combining the current pair of numbers with each pair stored in the hash table at the difference just calculated. Following this nested for loop, loop through the array again, this time starting at index zero all the way to the index of the first for loop. At each iteration, calculate the sum of the two numbers represented by the indices of the for loops and add it to the hash table if it isn't already there; then add the pair of indices to the array that the sum in the hash table maps to.

Note:
- From ith index we move in left (i-1 to 0) & right (i+1 to n-1)  direction
- Move in right direction & check if the current two element sum is present in map 
- If present in map its means that map two elements & current two elements sum is equals to targetSum.
- Move is the left direction and push targetSum - current two elements

#### IMP: 
>***Why pushing targetSum - two elements sum value in left direction only ?***
>Because to avoiding repeate calculation
>Ex:
> `arr = [2,4,5,8]`
>`if i=1(4)`
>`Right -> : arr[i]+arr[i+1] i.e (4,5)`
>`now i=2(5)`
>`Left. <-  : arr[i] + arr[i-1] i.e (5,4)`

> Conclusion: We are calculating 5,4 & 4,5 i.e index(1,2), two times but in actual is should in calculated onces.

```cpp
#include <vector>
using namespace std;

vector<vector<int>> fourNumberSum(vector<int> array, int targetSum) {
  vector<vector<int>> res;
  int n=array.size();
  if(n<=3) return res;
  map<int,vector<vector<int>>>m;
  for(int i=1;i<n-1;i++){
    int j=i-1;
    int k=i+1;
    while(k<n){
      int remaingTwo=array[i]+array[k];
      if(m.find(remaingTwo)!=m.end()){       
        vector<vector<int>> currentMap;
        currentMap=m[remaingTwo];
        for(int idx=0;idx<currentMap.size();idx++){
          vector<int> temp;
          temp=currentMap[idx];
          temp.push_back(array[i]);
          temp.push_back(array[k]);
          res.push_back(temp); 
        }
      }
      k++;
    }
    while(j>=0){
      vector<vector<int>> currentStoreMap;
      vector<int> temp;
      temp.push_back(array[i]);
      temp.push_back(array[j]);
      int targetMinusValue=targetSum-(array[i]+array[j]);
      if(m.find(targetMinusValue)!=m.end()){
        currentStoreMap=m[targetMinusValue];
      }
      currentStoreMap.push_back(temp);
      m[targetMinusValue]=currentStoreMap;
      j--;
    }
    
    }
  return res;
}

```




