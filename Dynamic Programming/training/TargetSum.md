Question Link: https://leetcode.com/problems/target-sum/

Video Link: https://www.youtube.com/watch?v=ot_XBHyqpFc&list=PL_z_8CaSLPWekqhdCPmFohncHwz8TY2Go&index=11

Complexity : time O(n*sum) | space O(n*sum)

```cpp
class Solution {
public:
    int countSubsetSum(vector<int> &arr,int n,int sum){
      vector<vector<int>>res(n+1,vector<int>(sum+1,0));
      for(int j=0;j<=sum;j++){
          res[0][j] = 0;
      }
      for(int i=0;i<=n;i++){
        res[i][0] = 1;
      }
        
      for(int i=1;i<=n;i++){
          //0 <= sum(nums[i]) <= 1000
          //-1000 <= target <= 1000
          //we did abs(target). means 0<=traget<=1000 
          //so now our range is from 0-sum
        for(int j=0;j<=sum;j++){
          if(arr[i-1] <= j){
            res[i][j] = res[i-1][j-arr[i-1]] + res[i-1][j];
          }else{
            res[i][j] = res[i-1][j];
          }
        }
      }
      return res[n][sum];

    }
    int findTargetSumWays(vector<int>& nums, int target) {
         int sum =0;
         /* 1. Basically, we'll be dividing array into two subsets such that their difference is given (S1-S2 = diff) -(i)
           2. Also, S1+S2 = total sum of array -(ii)
           3. From (i) + (ii) -> S1 = (diff+sum_of_array)/2 
           4. We use subset sum problem to further pass this reduced sum and calculate
        */
		
		//handle edge cases
         target = abs(target);
         int n = nums.size();
          for(int i=0;i<n;i++){
            sum+=nums[i];
          }
         //edge case when we have to avoid target > sum (not possible) and negative array exception
          if( sum < target ) return 0;
          if( (target+sum)%2 != 0 ) return 0;
          int reqSum = (sum+target)/2;
          return countSubsetSum(nums,n,reqSum);
    }
};
```
