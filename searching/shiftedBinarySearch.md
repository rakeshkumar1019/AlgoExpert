T.C : O(logn+logn)

S.C : O(1)


```cpp
#include <vector>
using namespace std;
int binarySearch(vector<int> array,int val,int start,int end){
  int n=array.size();
  int left=start;
  int right=end;
  while(left<=right){
    int mid= left+(right-left)/2;
    if(array[mid]==val){
      return mid;
    }else if(array[mid] < val){
      left=mid+1;
    }else{
      right=mid-1;
    }
  }
  return -1;
}

int getPivot(vector<int> array){
  int n=array.size();
  int left=0;
  int right=n-1;
  if(n==1) return array[0];
  while(left<=right){
    int mid=left+(right-left)/2;
    if(array[mid] < array[(mid+n-1)%n] && array[mid]< array[(mid+1)%n]){
      return mid;
    }else if( array[0]<= array[mid]){
      left=mid+1;
    }else if( array[n-1] >= array[mid]){
      right=mid-1;
    }
  }
  return array[0];
}
int shiftedBinarySearch(vector<int> array, int target) {
  int n= array.size();
  int pivot=getPivot(array);
  if( target >= array[pivot] && target <= array[n-1]){
    return binarySearch(array,target,pivot,n-1);
  }else{
    return binarySearch(array,target,0,pivot-1);
  }
}

```
