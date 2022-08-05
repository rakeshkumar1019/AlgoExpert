```cpp
#include<iostream>
using namespace std;
int exponent(int base,int power){
  if(power==0) return 1;
  if(power==1) return 2;
  return 2* exponent(base,power-1);
}
int main(){
  int base,power;
  cin>>base>>power;
  cout<<exponent(base,power);
}

```
