Question Link:
1. https://www.geeksforgeeks.org/printing-longest-common-subsequence/
2. https://www.youtube.com/watch?v=x5hQvnUcjiM&list=PL_z_8CaSLPWekqhdCPmFohncHwz8TY2Go&index=23

Complexity:
- time & space O(n*m)


```cpp
#include<bits/stdc++.h>
using namespace std;
string printLCS(string text1,string text2, int n,int m){
  vector<vector<int>>res(n+1,vector<int>(m+1,0));
  for(int i=0;i<=n;i++){
    res[i][0] =0;
  }
  for(int j=0;j<=m;j++){
    res[0][j] =0;
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
  string output = "";
  int i = n;
  int j = m;
  while( i > 0  && j > 0 ){
    if(text1[i-1] == text2[j-1]){
       output = output+text1[i-1];
       i--;
       j--;
    }else{
      if(res[i-1][j] > res[i][j-1]){
        i--;
      }else{
        j--;
      }
    }
  }
  reverse(output.begin(), output.end());
  return output;

  
}
int main(){
  string text1,text2;
  cin>>text1>>text2;
  int n = text1.size();
  int m = text2.size();
  cout<<printLCS(text1,text2,n,m);


}

```
