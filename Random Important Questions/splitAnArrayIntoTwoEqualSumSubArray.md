Question Link: https://www.geeksforgeeks.org/split-array-two-equal-sum-subarrays/

Video Link: https://www.youtube.com/watch?v=RZO6oR443nQ

Complexity: 
- time: O(n)
- space: O(1)

```cpp
#include<bits/stdc++.h>
using namespace std;
int minNoOfCoins(vector<int> coins,int n, int sum){
   vector<vector<int>>res(n+1,vector<int>(sum+1,0));
   for(int j=0;j<=sum;j++){
     res[0][j] = INT_MAX-1;
   }
   for( int i=1;i<=n;i++){
     res[i][0] = 0;
   }
   for(int j=1;j<=sum;j++){
     if(j%coins[0] == 0){
       res[1][j] = j/coins[0];
     }else{
       res[1][j] = INT_MAX-1;
     }
   }
   for(int i=2;i<=n;i++){
     for(int j=1;j<=sum;j++){
         if(coins[i-1] <= j ){
           res[i][j] = min(1+res[i][j-coins[i-1]],res[i-1][j]);
         }else{
           res[i][j] = res[i-1][j];
         }
     }
   }
   for(auto x: res){
     for(int y: x){
       cout<<y<<" ";
     }cout<<endl;
   }
   if(res[n][sum] == INT_MAX-1){
     return -1;
   }else{
     return res[n][sum];
   }
}
int main(){
  int n,sum;
  cin>>n>>sum;
  vector<int> coins;
  for(int i=0;i<n;i++){
    int input;
    cin>>input;
    coins.push_back(input);
  }
  cout<<minNoOfCoins(coins,n,sum)<<endl;
}

```
