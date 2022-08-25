Question Link: https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/
Video Link: https://www.youtube.com/watch?v=4WmTRFZilj8&t=1231s
T.C : O(logn)

S.C : O(1)
```cpp
class Solution {
public:
    int findMin(vector<int>& nums) {
        int n=nums.size();
        int left=0;
        int right=n-1;
        if(n==1) return nums[0];
        while(left<=right){
            int mid=left+(right-left)/2;
            if ( nums[mid] < nums[(mid+n-1)%n] && nums[mid] < nums[(mid+1)%n] ) {
                return nums[mid];
            } else if ( nums[0] <= nums[mid]){
                left=mid+1;
            } else if ( nums[n-1] >= nums[mid]){
                right=mid-1;
            }
        }
        return nums[0];
    }
};
```
