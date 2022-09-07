Question Link: https://www.geeksforgeeks.org/count-of-subsets-with-sum-equal-to-x/

Video Link: https://www.youtube.com/watch?v=F7wqWbqYn9g&list=PL_z_8CaSLPWekqhdCPmFohncHwz8TY2Go&index=9

Complexity: 
1. Brute Force: time O(2^n) | space O(n) stack
2. Dp : time: O(n*sum) | space O(n*sum)

```cpp
#include<iostream>
#include<vector>
using namespace std;
vector<vector<int>> res(100,vector<int>(100,-1));
int countSumSetSum(vector<int> &arr, int n ,int sum){
  for(int j=0;j<=sum;j++){
    res[0][j] = 0;
  }
  for(int i=0;i<=n;i++){
    res[i][0] =1;
  }
  for(int i=1;i<=n;i++){
    for(int j=1;j<=sum;j++){
      if(arr[i-1] <= j){
        res[i][j] = res[i-1][j-arr[i-1]] + res[i-1][j];
      }else if( arr[i-1] > j){
        res[i][j] = res[i-1][j];
      }
    }
  }
  return res[n][sum];
}
int main(){
  int n,sum;
  cin>>n>>sum;
  vector<int> arr;
  for(int i=0;i<n;i++){
    int input;
    cin>>input;
    arr.push_back(input);
  }
  cout<<countSumSetSum(arr,n,sum);
}

```
