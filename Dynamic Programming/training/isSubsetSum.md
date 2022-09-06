Question Link: https://www.geeksforgeeks.org/subset-sum-problem-dp-25/

Complexity: 
 1. Brute Force: time O(2^n) | space O(n) stack
 2. Optimal : time O(n*sum) | space O(n*sum)

```cpp
#include<iostream>
#include<vector>
using namespace std;
bool isSubSetSum(vector<int> &items,int n, int sum){
  if( n == 0 ) return false;
  if( sum == 0 ) return true;
  if( items[n-1] <= sum ){
    return isSubSetSum(items,n-1,sum-items[n-1]) || isSubSetSum(items,n-1,sum);
  } else if ( items[n-1] > sum ){
    return isSubSetSum(items ,n-1,sum);
  }
}
bool isSubSetSumRecursiveDp(vector<int> &items,int n,int sum,vector<vector<int>> &res){
  if( n == 0 ) return false;
  if( sum == 0 ) return true;
  if( res[n][sum] != -1 ) return res[n][sum];
  if(items[n-1] <= sum ){
    res[n][sum] = isSubSetSumRecursiveDp(items,n-1,sum-items[n-1],res) || isSubSetSumRecursiveDp(items,n-1,sum,res);
    return res[n][sum];
  }else if( items[n-1] > sum ){
    res[n][sum] = isSubSetSumRecursiveDp(items,n-1,sum,res);
    return res[n][sum];
  }
}
bool isSubSetItrativeDp(vector<int> &items, int n ,int sum ,vector<vector<bool>> &res){
  //right side
  for(int j=0;j<= sum;j++){
       res[0][j] = false;
  }
  //down side
  for(int i =0;i<=n;i++){
    res[i][0] = true;
  }
  // res[0][0] will be true now
  for(int i=1;i<=n;i++){
    for(int j=1;j<=sum;j++){
      if( items[i-1] <= j ){
        res[i][j] = res[i-1][j-items[i-1]] || res[i-1][j];
      } else if( items[i-1] > j ){
        res[i][j] = res[i-1][j];
      }
    }
  }
  return res[n][sum];
}
int main(){
   int n,sum;
   cin>>n>>sum;
   vector<int> items;
   for(int i=0;i<n;i++){
     int temp;
     cin>>temp;
     items.push_back(temp);
   }
   cout<<isSubSetSum(items,n,sum)<<endl;
  //  vector<vector<int>>res(n+1,vector<int>(sum+1,-1));
  //  cout<<isSubSetSumRecursiveDp(items,n,sum,res)<<endl;

   vector<vector<bool>>res(n+1,vector<bool>(sum+1,false));
   cout<<isSubSetItrativeDp(items,n,sum,res)<<endl;

}

```
