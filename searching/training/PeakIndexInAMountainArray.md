Question Link: https://leetcode.com/problems/peak-index-in-a-mountain-array/submissions/

T.C: O(logn)

S.C: O(1)



```cpp
class Solution {
public:
    int peakIndexInMountainArray(vector<int>& arr) {
        int n= arr.size();
        if(n<=0) return -1;
        int left=0;
        int right=n-1;
        while(left<=right){
            int mid=left+(right-left)/2;
            if(mid>0 || mid<=n-2){
                if(arr[mid]>arr[mid+1] && arr[mid]> arr[mid-1]){
                    return mid;
                }else if(arr[mid] < arr[mid+1]){
                    left=mid+1;
                }else{
                    right=mid-1;
                }
            }else if(mid==0 && arr[mid]>arr[mid+1]){
                return mid;
            }else if(mid==n-1 && arr[mid]>arr[mid-1]){
                return mid;
            }
        }
        return -1;
    }
};
```
