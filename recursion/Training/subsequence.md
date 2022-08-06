```cpp
#include<bits/stdc++.h>
using namespace std;
void subsequence(string str,string &output,int index){
  if(index==str.length()){
    cout<<output<<endl;
    return;
  }
  subsequence(str,output,index+1);
  output.push_back(str[index]);
  subsequence(str,output,index+1);
  output.pop_back();
}
int main(){
  string str="abc";
  string output="";
  subsequence(str,output,0);
}

```
