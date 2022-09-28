Question Link: 
1. https://www.geeksforgeeks.org/longest-common-substring-dp-29/
2. https://www.interviewbit.com/blog/longest-common-substring/
3. https://leetcode.com/discuss/interview-question/1273766/longest-common-substring

Complexity:
- time & space O(n*m) 

```cpp

#include<bits/stdc++.h>
using namespace std;
int getLCSubstring(string text1,string text2,int n,int m){
  vector<vector<int>>res(n+1,vector<int>(m+1,0));
  for(int i=0;i<=n;i++){
    res[i][0] = 0;
  }
  for(int j=0;j<=m;j++){
    res[0][j] = 0;
  }
  int result = INT_MIN;
  for(int i=1;i<=n;i++){
    for(int j=1;j<=m;j++){
      if(text1[i-1] == text2[j-1]){
        res[i][j] = 1+res[i-1][j-1];
        result = max(result,res[i][j]);
      }else{
        res[i][j] = 0;
      }
    }
  }
  return result != INT_MIN ? result : 0 ;
}
int main(){
  string text1,text2;
  cin>>text1>>text2;
  int n = text1.size();
  int m = text2.size();
  cout<<getLCSubstring(text1,text2,n,m);
}

```
