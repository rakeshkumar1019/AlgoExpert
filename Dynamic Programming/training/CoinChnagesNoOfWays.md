Question Link : https://www.geeksforgeeks.org/coin-change-dp-7/

Video Link: https://www.youtube.com/watch?v=I4UR2T6Ro3w&list=PL_z_8CaSLPWekqhdCPmFohncHwz8TY2Go&index=15

>Complexity: O(n*sum)


```cpp
#include<iostream>
#include<bits/stdc++.h>
using namespace std;
int noOfCoinChange(vector<int> arr,int n, int sum){
  vector<vector<int>> res(n+1,vector<int>(sum+1,0));
  for(int j=0;j<=sum;j++){
    res[0][j] = 0;
  }
  for(int i=0;i<=n;i++){
    res[i][0] = 1;
  }
  for(int i=1;i<=n;i++){
    for(int j=1;j<=sum;j++){
      if(arr[i-1]<=j){
        res[i][j] = res[i][j-arr[i-1]] + res[i-1][j];
      }else{
        res[i][j] = res[i-1][j];
      }
    }
  }
  return res[n][sum];
}
int main(){
  int n,sum;
  cin>>n>>sum;
  vector<int>arr;
  for(int i=0;i<n;i++){
    int input;
    cin>>input;
    arr.push_back(input);
  }
  cout<<noOfCoinChange(arr,n,sum)<<endl;
}

```
