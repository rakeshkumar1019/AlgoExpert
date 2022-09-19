Queston Link: Min No of coins to make sum

Youtube: https://www.youtube.com/watch?v=rMfOgY07TFs&list=PL_z_8CaSLPWekqhdCPmFohncHwz8TY2Go&index=17

> Complexity: time | sum => O(n*sum)

```cpp
 class Solution {
public:
    int coinChange(vector<int>& coins, int sum) {
         int n = coins.size();
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
           if(res[n][sum] == INT_MAX-1){
             return -1;
           }else{
             return res[n][sum];
           }
        
    }
};
```
