Question Link: https://www.geeksforgeeks.org/shortest-common-supersequence/

```cpp
#include<bits/stdc++.h>
using namespace std;

int LCS(string str1, string str2,int n ,int m){
    vector<vector<int>>res(n+1,vector<int>(m+1,0));
    for(int i=0;i<=n;i++){
        res[i][0] = 0;
    }
    for(int j=0;j<=m;j++){
        res[0][j] = 0;
    }
    for(int i=1;i<=n;i++){
        for(int j=1;j<=m;j++){
            if(str1[i-1] == str2[j-1]){
                res[i][j] = 1+res[i-1][j-1];
            }else{
                res[i][j] = max(res[i-1][j],res[i][j-1]);
            }
        }
    }
    return res[n][m];
}
int shortestCommonSupersequence(string str1, string str2) {
    int n = str1.size();
    int m = str2.size();
    int lcs = LCS(str1,str2,n,m);
    int total =n+m;
    return total - lcs;
}

int main(){
   string str1,str2;
   cin>>str1>>str2;
   cout<<shortestCommonSupersequence(str1,str2);
}

```
