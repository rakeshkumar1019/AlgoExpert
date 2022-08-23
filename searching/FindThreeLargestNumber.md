T.C: O(N) we can ignore 3 itration

S.C: O(3) 

```cpp
#include <vector>
using namespace std;
void shifAndUpdate(vector<int> &threeLargest,int num,int idx){
  for(int i=0;i<=idx;i++){
    if(idx==i){
      threeLargest[i]=num;
    }else{
      threeLargest[i]=threeLargest[i+1];
    }
  }
}
void updateThreeLargest(vector<int> &threeLargest,int num){
  if(num>threeLargest[2]){
    shifAndUpdate(threeLargest,num,2);
  }else if(num > threeLargest[1]){
    shifAndUpdate(threeLargest,num,1);
  }else if(num>threeLargest[0]){
    shifAndUpdate(threeLargest,num,0);
  }
}
vector<int> findThreeLargestNumbers(vector<int> array) {
 vector<int> threeLargest(3,INT_MIN);
  for(int i=0;i<array.size();i++){
    updateThreeLargest(threeLargest,array[i]);
  }
  return threeLargest;
}

```
