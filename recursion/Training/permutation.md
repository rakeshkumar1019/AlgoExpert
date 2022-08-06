```cpp
#include<bits/stdc++.h>
using namespace std;
void permutation(string str,int idx){
  if(idx==str.length()-1){
    cout<<str<<endl;
  }
  for(int i=idx;i<str.length();i++){
    swap(str[i],str[idx]);
    permutation(str,idx+1);
    swap(str[i],str[idx]);

  }
}
int main(){
  string str="abc";
  permutation(str,0);
}

```
