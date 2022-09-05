```cpp
#include<iostream>
#include <bits/stdc++.h>
using namespace std;
int res[100][100];
int knapSackRecursive(int wt[], int val[], int W, int n ){
  if( n==0 || W == 0 ){
    return 0;
  }
  if( res[n][W] != -1 ) {
    return res[n][W];
  }

  if( wt[n-1] <= W ){
    res[n][W] = max( val[n-1]+knapSackRecursive(wt,val,W-wt[n-1],n-1),knapSackRecursive(wt,val,W,n-1));
    return res[n][W];
  }else if(wt[n-1] > W){
    res[n][W] = knapSackRecursive(wt,val,W,n-1);
    return res[n][W];
  }
} 

int knapSack(int wt[], int val[], int W, int n ){
  if( n == 0 || W == 0 ) return 0;
  //base condition
  for(int i=0;i<=n;i++){
    res[i][0] = 0;
  }
  for(int i=0;i<=W;i++){
    res[0][i] = 0;
  }

  for( int i=1;i<=n;i++){
    for( int j=1;j<=W;j++){
      if(wt[i-1] <= j ){
        res[i][j] = max(val[i-1]+res[i-1][j-wt[i-1]],res[i-1][j]);
      }else if( wt[i-1] >j ){
        res[i][j] = res[i-1][j];
      }
    }
  }
  return res[n][W];
}

int main(){
  int wt[4] = {2,3,6,7};
  int val[4] = {1,4,5,6};
  int W = 10;
  int n = 4;
  for(int i=0;i<100;i++){
    for(int j=0;j<100;j++){
      res[i][j]=-1;
    }
  }
  cout<<knapSackRecursive(wt,val,W,n)<<endl;  
  // cout<<knapSack(wt,val,W,n)<<endl;  

}

```
