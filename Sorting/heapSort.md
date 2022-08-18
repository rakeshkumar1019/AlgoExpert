T.C : O(nlogn)

```cpp
#include <vector>
using namespace std;
void heapify(vector<int> &array,int n,int index){
  int largestIndex=index;
  int leftIndex=2*index+1;
  int rightIndex=2*index+2;

  if(leftIndex < n && array[largestIndex]<array[leftIndex]){
    largestIndex=leftIndex;
  }
  if(rightIndex < n && array[largestIndex]<array[rightIndex]){
    largestIndex=rightIndex;
  }
  if(largestIndex!=index){
    swap(array[largestIndex],array[index]);
    heapify(array,n,largestIndex);
  }
}
vector<int> heapSort(vector<int> array) {
  int size=array.size();
  //build heap
  for(int i=size/2-1;i>=0;i--){
    heapify(array,size,i);
  }
  
  for(int i=size-1;i>0;i--){
    swap(array[0],array[i]);
    heapify(array,i,0);
  }
  return array;
}

```
