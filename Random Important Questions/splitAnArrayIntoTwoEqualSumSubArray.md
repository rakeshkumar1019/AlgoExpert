Question Link: https://www.geeksforgeeks.org/split-array-two-equal-sum-subarrays/

Video Link: https://www.youtube.com/watch?v=RZO6oR443nQ

Complexity: 
- time: O(n)
- space: O(1)

```cpp
#include<bits/stdc++.h>
using namespace std;
int getPartitionIndex(vector<int> &array,int n){
  int totalSum=0;
  for(int i=0;i<n;i++){
    totalSum+=array[i];
  }
  int rightSum=0;
  for(int i=n-1;i>=0;i--){
    rightSum+=array[i];
    totalSum-=array[i];
    if(rightSum == totalSum){
      return i;
    }
  }
  return -1;
}
vector<vector<int>> splitEqualSumSubArray(vector<int> array){
  int n = array.size();
  vector<vector<int>> res;
  if( n == 0 ) return res;
  int splitIndex = getPartitionIndex(array,n);
  if( splitIndex == -1){
    cout<<" No Possible"<<endl;
    return res;
  }else{
    vector<int> one,two;
    for(int i = 0;i<splitIndex;i++){
       one.push_back(array[i]);
    }
    for(int i=splitIndex;i<n;i++){
      two.push_back(array[i]);
    }
    res.push_back(one);
    res.push_back(two);

  }
}
int main(){
  int n;
  cin>>n;
  vector<int> array;
  for(int i=0;i<n;i++){
    int input;
    cin>>input;
    array.push_back(input);
  }
  vector<vector<int>> res = splitEqualSumSubArray(array);
  for(auto x: res){
    for(auto j : x){
      cout<<j<<" ";
    }cout<<endl;
  }
  
}

```
