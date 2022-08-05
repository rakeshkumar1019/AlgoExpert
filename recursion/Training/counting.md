```cpp
#include<iostream>
using namespace std;
void printNumberAscendingly(int n){
  if(n==0) return;
  printNumberAscendingly(n-1);
  cout<<n<<" ";
}
void printNumberDescendingly(int n){
  if(n==0) return;
  cout<<n<<" ";
  printNumberDescendingly(n-1);
}
int main(){
  int n;
  cin>>n;
  printNumberAscendingly(n);
  cout<<endl;
  printNumberDescendingly(n);
}

```
