Question Link: 
1. https://www.geeksforgeeks.org/longest-common-subsequence-dp-4/
2. https://leetcode.com/problems/longest-common-subsequence/

Complexity: 
1. Brute Force Approch: time O(2^n) | space O(n) stack
2. Dp Approch : time & space O(n*m)



```cpp
#include<bits/stdc++.h>
using namespace std;
//recursive 
int getLongestCommonSubsequence(string X,string Y,int n,int m){
  if( n == 0 || m == 0 ) return 0;
  if(X[n-1] == Y[m-1]){
    return 1+getLongestCommonSubsequence(X,Y,n-1,m-1); 
  }else{
    return max(getLongestCommonSubsequence(X,Y,n-1,m),getLongestCommonSubsequence(X,Y,n,m-1));
  }
}
int LCS(string text1, string text2,int n,int m){
  vector<vector<int>>res(n+1,vector<int>(m+1,0));
  for(int i=0;i<=n;i++){
    res[i][0] = 0;
  }
  for(int j=0;j<=m;j++){
    res[0][j]=0;
  }
  for(int i=1;i<=n;i++){
    for(int j=1;j<=m;j++){
      if( text1[i-1] == text2[j-1] ){
          res[i][j] = 1+res[i-1][j-1];
      }else{
         res[i][j] = max(res[i-1][j],res[i][j-1]);
      }
    }
  }
  return res[n][m];
}
int main(){
  string X,Y;
  cin>>X>>Y;
  int n =X.size();
  int m =Y.size();
  // cout<<getLongestCommonSubsequence(X,Y,n,m);
  cout<<LCS(X,Y,n,m);
}

```
