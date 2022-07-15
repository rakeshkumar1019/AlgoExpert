# **Two Number Sum**
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/twoSumNuber.png)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/twoSumNuber.png)
### **Burute Force Approch**
Complexity :-
- Time:    O(n^2)
- Space : O(1)

```cpp
vector<int> twoNumberSum(vector<int>array,int targetSum){
  vector<int> res;
  int n=array.size();
  for(int i=0;i<n-1;i++){
    for(int j=i+1;j<n;j++){
      if(array[i]+array[j]==targetSum){
        res.push_back(array[i]);
        res.push_back(array[j]);
        break;
      }
    }
  }
  return res;
}
```
#### Optimal Approch 1: Using HashTable
Complexity :-
- Time:    O(n)
- Space : O(n)
```cpp
vector<int> twoNumberSum(vector<int>array,int targetSum){
  vector<int> res;
  int n=array.size();
  map<int,bool>m;
  for(int i=0;i<n;i++){
    if(m.find(array[i])!=m.end()){
      res.push_back(array[i]);
      res.push_back(targetSum-array[i]);
      break;
    }
    m[targetSum-array[i]]=true;
  }
  return res;
}
```
#### Optimal Approch: Using Two Pointers
Complexity :-
 - Time:    O(nlogn)
 - Space : O(1)
```cpp
vector<int> twoNumberSum(vector<int>array,int targetSum){
  vector<int> res;
  int n=array.size();
  sort(array.begin(),array.end());
  int left=0;
  int right=n-1;
  while(left<right){
    if(array[left]+array[right]==targetSum){
      res.push_back(array[left]);
      res.push_back(array[right]);
      break;
    }
    if(array[left]+array[right]>targetSum){
      right--;
    }
    if(array[left]+array[right]<targetSum){
      left++;
    }
  }
  return res;
}
```

