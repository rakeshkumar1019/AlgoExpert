# Validate Subsequence
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/validatesubsequence.png)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/validatesubsequence.png)
#### Approch 1: Using Two For loops
Complexity :
- Time: O(n^2)
- Space: O(1)

#### Approch 2: Using Stack
Complexity :
- Time: O(n)
- Space: O(n)
#### Optimal Approch : Uisng 1 loop
Complexity :
- Time: O(n)
- Space: O(1)
```cpp
bool isValidSubsequence(vector<int> array, vector<int> sequence) {
int n=array.size();
  int m=sequence.size();
  int j=0;
  for(int i=0;i<n;i++){
    if(array[i]==sequence[j]){
      j=j+1;
    }
  }
  if(j==m){
    return true;
  }
  return false;
}
```
