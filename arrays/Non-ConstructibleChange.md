# Non-Constructible Change
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/nonConstribleChange.png)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/nonConstribleChange.png)
#### Brute Force Approch : 1,2,3 ...K 
Start from 1 to K, Check number can be made from the above array;
```cpp
int change=1;
while(currentChangeCanBeCreated(change)){
	change++;
}
return change
```
Note: Create this function `currentChangeCanBeCreated(change)` is very complicated & un-optimised

Complexity: 
- Time: O(K*`currentChangeCanBeCreated()`)
- Space:O(1)

#### Optimal Approch: Pattern Finding
> **IMP: Understand Pattern**
```cpp
canCreateChange=k
if(coins[i] > canCreateChange+1){
	return canCreateChange+1;
}
```
EX: `coins = [1,2 5]`
Imp: `sort` first
```cpp
	canCreateChange=0;
	index: 0 , coin=1
	canCreateChange+1 i.e (0+1) ! > coin , so canCreateChange+=coin
```
```cpp
	canCreateChange=1
    index: 1 ,coin=2
	canCreateChange+1 i.e (1+1)!> coin , so canCreateChange+=coin
```
```cpp
	canCreateChange=3
	index: 2 ,coin=5
	canCreateChange+1 i.e (3+1) > coin , we can't create canCreateChange+1
```
So, `4` is the minimum  coin 

#### Code:
```cpp
#include <vector>
using namespace std;

int nonConstructibleChange(vector<int> coins) {
 int n=coins.size();
  sort(coins.begin(),coins.end());
  int canCreateChange=0;
  for(int i=0;i<n;i++){
    if(coins[i] > canCreateChange+1){
      return canCreateChange+1;
    }
    canCreateChange+=coins[i];
  }
  return canCreateChange+1;
}

```
Complexity: 
- Time: O(nlogn)
- Space: O(1)
