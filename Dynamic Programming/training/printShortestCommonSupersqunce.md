Question Link: https://leetcode.com/problems/shortest-common-supersequence/

Complexity: 
- Time & space. O(n*m)


```cpp
class Solution {
public:
    
string printSCS(string text1,string text2,int n ,int m){
      vector<vector<int>>res(n+1,vector<int>(m+1,0));
      for(int i=0;i<=n;i++){
        res[i][0] =0;
      }
      for(int j=0;j<=m;j++){
        res[0][j] =0;
      }
      for(int i=1;i<=n;i++){
        for(int j=1;j<=m;j++){
          if(text1[i-1] == text2[j-1]){
            res[i][j] = 1+res[i-1][j-1];
          }else{
            res[i][j] = max(res[i-1][j],res[i][j-1]);
          }
        }
      }

      string output = "";
      int i = n;
      int j = m;
      while(i >0 && j>0 ){
        if(text1[i-1] == text2[j-1]){
          output+=text1[i-1];
          i--;
          j--;
        }else{
          if(res[i-1][j] > res[i][j-1]){
            output+=text1[i-1];
            i--;
          }else{
            output+=text2[j-1];
            j--;
          }
        }
      }
      while( i > 0){
        output+=text1[i-1];
        i--;
      }

      while( j>0 ){
        output+=text2[j-1];
        j--;
      }

      reverse(output.begin(),output.end());
      return output;
    } 
    string shortestCommonSupersequence(string str1, string str2) {
        return printSCS(str1,str2,str1.size(),str2.size());
    }
};
```
