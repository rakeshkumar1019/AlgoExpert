```cpp
#include<iostream>
#include<vector>
using namespace std;
bool isSortedHelper(vector<int> arr,int idx){
  //base case
  if(idx==arr.size()) return true;
  if(arr[idx]>arr[idx-1]){
    return isSortedHelper(arr,idx+1);
  }else{
    return false;
  }

}
bool isSorted(vector<int> arr){
  if(arr.size()==1) return true;
  return isSortedHelper(arr,1);

}
int main(){
  int n;
  cin>>n;
  vector<int> arr;
  for(int i=0;i<n;i++){
    int temp;
    cin>>temp;
    arr.push_back(temp);
  }
  cout<<isSorted(arr)<<endl;
}

```
