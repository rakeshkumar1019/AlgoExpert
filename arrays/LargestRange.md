# Largest Range
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/largestRange.png)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/largestRange.png)

#### Brute Force Approch: Using Sort
##### Complexity:
- Time : O(nlogn)
- Space: O(1)

#### Optimal Approch : Using Map & isVisited Concept
##### Complexity:
- Time : O(n)
- Space: O(n)

##### Hint1: 
>How can you use a hash table to solve this problem with an algorithm that runs in linear time?

##### Hint2: 
>Iterate through the input array once, storing every unique number in a hash table and mapping every number to a falsy value. This hash table will not only provide for fast access of the numbers in the input array, but it will also allow you to keep track of "visited" and "unvisited" numbers, so as not to unnecessarily repeat work.

##### Hint3:
>Iterate through the input array once more, this time stopping at every number to check if the number is marked as "visited" in the hash table. If it is, skip it; if it isn't, start expanding outwards from that number with a left number and a right number, continuously checking if those left and right numbers are in the hash table (and thus in the input array), and marking them as "visited" in the hash table if they are. This should allow you to quickly find the largest range in which the current number is contained, all the while setting you up not to perform unnecessary work later.

```cpp
#include <vector>
using namespace std;

vector<int> largestRange(vector<int> array) {
   vector<int> res={-1,-1};
   int n=array.size();
   if(n==0){
     return res;
   }
   if(n==1){
     res[0]=array[0];
     res[1]=array[0];
     return res;
   }
   int maxLength=INT_MIN;
   map<int,bool> m;
   for(int i=0;i<n;i++){
     m[array[i]]=true;
   }
   for(int i=0;i<n;i++){
     int currNum=array[i];
     if(m[currNum]){
       int currLength=1;
       int left=currNum;
       int right=currNum;
       while(m[left-1]){
         m[left-1]=false;
         left--;
         currLength++;
       }
       while(m[right+1]){
         m[right]=false;
         right++;
         currLength++;
       }
       if(currLength>maxLength){
         res[0]=left;
         res[1]=right;
         maxLength=currLength;
       }
     }
   }
  return res;
}

```
