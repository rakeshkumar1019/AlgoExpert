# Merge Sort
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/MergeSort.png)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/MergeSort.png)

#### Complexity:
>Best: O(nlog(n)) time | O(n) space - where n is the length of the input array
>
>Average: O(nlog(n)) time | O(n) space - where n is the length of the input array
>
>Worst: O(nlog(n)) time | O(n) space - where n is the length of the input array

```cpp
#include <vector>
using namespace std;
void merge(vector<int> &res,int l,int m,int r){
  if(l>=r){
   return; 
  } 
  int size=r-l+1;
  int i=l;
  int j=m+1;
  vector<int> temp(size,0);
  int k=0;
  while(i<=m && j<=r){
    if(res[i]<=res[j]) { 
      temp[k]=res[i];
      i++; 
      k++;
    }else{ 
      temp[k]=res[j]; 
      j++; 
      k++;
    }
  }
  while(i<=m){
   temp[k]=res[i];
   i++; 
   k++;
  } 
  while(j<=r){
    temp[k]=res[j]; 
    j++; 
    k++;
  }
  
  for(k=0;k<size;k++){
    res[l+k]=temp[k];
  }
}
void mergeSortArray(vector<int> &res,int l,int r){
  if(l>=r){
   return; 
  } 
  int m=(r-l)/2+l;
  mergeSortArray(res,l,m);
  mergeSortArray(res,m+1,r);
  merge(res,l,m,r);
}
vector<int> mergeSort(vector<int> array) {
  int n=array.size();
  if(n<=1) return array;
  vector<int> res=array;
  int l=0;
  int r=n-1;
  mergeSortArray(res,l,r);
  return res;
}

```

