```cpp
#include<iostream>
#include<bits/stdc++.h>
using namespace std;
void subsets(vector<int> arr,int idx,vector<int> &currentOutput){
  if(idx==arr.size()){
    for(int i=0;i<currentOutput.size();i++){
      cout<<currentOutput[i]<<" ";
    }
    cout<<endl;
    return;
  }
  subsets(arr,idx+1,currentOutput);//without
  currentOutput.push_back(arr[idx]);
  subsets(arr,idx+1,currentOutput); //with
  currentOutput.pop_back();
}
int main(){
  vector<int> arr={1,2,3};
  vector<int> currentOutput;
  subsets(arr,0,currentOutput);
}

```
