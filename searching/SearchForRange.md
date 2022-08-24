T.C : O(logn)+O(logn)

S.C :O(1) 

```cpp
#include <vector>
using namespace std;
int leftIndex(vector<int> array,int target){
  int left=0;
  int right=array.size()-1;
  int leftInd=-1;
  while(left<=right){
    int mid=left+(right-left)/2;
    if(array[mid]==target){
      leftInd=mid;
      right=mid-1;
    }else if(array[mid]<target){
      left=mid+1;
    }else{
      right=mid-1;
    }
  }
  return leftInd;
}
int rightIndex(vector<int> array,int target){
  int left=0;
  int right=array.size()-1;
  int rightInd=-1;
  while(left<=right){
    int mid=left+(right-left)/2;
    if(array[mid]==target){
      rightInd=mid;
      left=mid+1;
    }else if(array[mid]<target){
      left=mid+1;
    }else{
      right=mid-1;
    }
  }
  return rightInd;
}

vector<int> searchForRange(vector<int> array, int target) {
   vector<int> res;
   int leftOccur=leftIndex(array,target);
   int rightOccur=rightIndex(array,target);
   res.push_back(leftOccur);
   res.push_back(rightOccur);
   return res; 
  
}

```
