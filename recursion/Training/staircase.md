```cpp
#include<bits/stdc++.h>
using namespace std;
//time O(3^n)
int stairCase(int h){
  if(h==0) return 1;
  if(h==1) return 1;
  if(h<0) return 0;
  return stairCase(h-1)+stairCase(h-2)+stairCase(h-3);
}
int main(){
  int n=4;
  cout<<stairCase(n)<<endl;
}

```
