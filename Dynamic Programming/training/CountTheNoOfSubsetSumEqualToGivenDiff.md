>Question LinK: https://leetcode.com/discuss/interview-question/1271034/count-no-of-subsets-with-given-difference-dp
>
>Video  Link: https://www.youtube.com/watch?v=ot_XBHyqpFc&list=PL_z_8CaSLPWekqhdCPmFohncHwz8TY2Go&index=11
>
>Similar Question :https://leetcode.com/problems/target-sum/

Complexity : time O(n*sum) | space O(n*sum)

```cpp
#include<bits/stdc++.h>
using namespace std;
int countSubsetSum(vector<int>arr,int n,int sum){
  vector<vector<int>>res(n+1,vector<int>(sum+1,0));
  for(int j=0;j<=sum;j++){
      res[0][j] = 0;
  }
  for(int i=0;i<=n;i++){
    res[i][0] = 1;
  }
  for(int i=1;i<=n;i++){
    for(int j=1;j<=sum;j++){
      if(arr[i-1] <= j){
        res[i][j] = res[i-1][j-arr[i-1]] + res[i-1][j];
      }else{
        res[i][j] = res[i-1][j];
      }
    }
  }
  return res[n][sum];

}
int countSubsetSumDiffrenceEqualtoDiff(vector<int> arr,int n,int diff){
  int sum =0;
  for(int i=0;i<n;i++){
    sum+=arr[i];
  }
  //s1 - s2 =diff
  //s1 + s2 = sum
  //adding both
  //2s1 = diff+sum ==> s1 = diff+sum/2
  int reqSum = (diff+sum)/2;
  return countSubsetSum(arr,n,reqSum);

}
int main(){
  int n,diff;
  cin>>n>>diff;
  vector<int> arr;
  for(int i=0;i<n;i++){
    int inp;
    cin>>inp;
    arr.push_back(inp);
  }
  cout<<countSubsetSumDiffrenceEqualtoDiff(arr,n,diff)<<endl;
}

```
