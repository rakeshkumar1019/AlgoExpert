Question Link:https://www.geeksforgeeks.org/partition-a-set-into-two-subsets-such-that-the-difference-of-subset-sums-is-minimum/

Video Link: https://www.youtube.com/watch?v=-GtpxG6l_Mc&list=PL_z_8CaSLPWekqhdCPmFohncHwz8TY2Go&index=10

Complexity : time O(n*sum) | space O(n*sum)

```cpp
#include<iostream>
#include<vector>
#include<bits/stdc++.h>
using namespace std;
int findMinimumSubSetDiffrence(vector<int> arr,int n){
  int sum =0;
  for(int i=0;i<n;i++){
    sum+=arr[i];
  }
  vector<vector<bool>>res(n+1,vector<bool>(sum+1,false));
  for(int j=0;j<=sum;j++){
    res[0][j] = false;
  }
  for(int i=0;i<=n;i++){
    res[i][0]=true;
  }
  for(int i = 1;i<=n;i++){
    for(int j=1;j<=sum;j++){
      if(arr[i-1]<=j){
        res[i][j] = res[i-1][j-arr[i-1]] || res[i-1][j];
      }else{
        res[i][j]= res[i-1][j];
      }
    }
  }
  int minDiff=INT_MAX;
  for(int j = sum/2;j>=0;j--){
    if(res[n][j] == true){
      minDiff = min(minDiff,abs(sum-2*j));
    }
  }
  return minDiff;
}
int main(){
  int n;
  cin>>n;
  vector<int> arr;
  for(int i=0;i<n;i++){
    int temp;
    cin>>temp;
    arr.push_back(temp);
  }
  cout<<findMinimumSubSetDiffrence(arr,n)<<endl;
}

```
