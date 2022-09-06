Question Link:https://leetcode.com/problems/partition-equal-subset-sum

Complexity: O(n*sum) - time & space

```cpp
class Solution {
public:
    bool isSubSetSum(vector<int> &nums, int n ,int sum){
        vector<vector<bool>> res(n+1,vector<bool>(sum+1,false));
        for(int j=0;j<=sum;j++){
            res[0][j] = false;
        }
        for(int i=0;i<=n;i++){
            res[i][0] = true;
        }
        for(int i=1;i<=n;i++){
            for(int j=1;j<=sum;j++){
                if( nums[i-1] <= j ){
                  res[i][j] = res[i-1][j-nums[i-1]] || res[i-1][j];  
                }else if ( nums[i-1] > j ){
                  res[i][j] = res[i-1][j];
                }
            }
        }
        return res[n][sum];
    }
    bool canPartition(vector<int>& nums) {
        int sum = 0;
        int n= nums.size();
        if( n == 1 || n == 0 ) return false;
        for(int i=0;i<n;i++){
            sum+=nums[i];
        }
        
        if( sum%2 == 0 ){
            return isSubSetSum(nums,n,sum/2);
        }else{
            return false;
        }
    }
};
```
