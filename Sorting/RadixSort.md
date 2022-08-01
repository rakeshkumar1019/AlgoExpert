# Radix Sort
#### Complexity
>O(d * (n + b)) time | O(n + b) space - where n is the length of the input array, d is the max number of digits, and b is the base of the numbering system used
```
#include <vector>
using namespace std;
void coutingSort(vector<int> &array,int digit){
  int n=array.size();
  vector<int> countStoreNoofDigit(10,0);
  vector<int> storeElements(n,0);
  for(int i=0;i<n;i++){
    int columnIdx=array[i]/pow(10,digit);
    int currentDigitIndex= (columnIdx)%10;
    countStoreNoofDigit[currentDigitIndex]+=1;
  }
  for(int i=1;i<10;i++){
    countStoreNoofDigit[i]=countStoreNoofDigit[i]+countStoreNoofDigit[i-1];
  }

  for(int i=n-1;i>=0;i--){
    int columnIdx=array[i]/pow(10,digit);
    int currentIndex=(columnIdx)%10;
    countStoreNoofDigit[currentIndex]-=1;
    int currenetStoredIndex=countStoreNoofDigit[currentIndex];
    storeElements[currenetStoredIndex]=array[i];
  }
  for(int i=0;i<n;i++){
    array[i]=storeElements[i];
  }
  return;
}
vector<int> radixSort(vector<int> array) {
  int n= array.size();
  int maxElem=INT_MIN;
  for(int i=0;i<n;i++){
    maxElem=max(maxElem,array[i]);
  }
  int digit=0;
  while((maxElem/pow(10,digit))>0){
    coutingSort(array,digit);
    digit++;
  }
  return array;
}

```
