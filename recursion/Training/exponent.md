```cpp
#include<iostream>
using namespace std;
//O(n)
int exponent(int base,int power){
  if(power==0) return 1;
  if(power==1) return 2;
  return 2* exponent(base,power-1);
}
//O(logn)
int fastExponent(int base,int power){
  if(power==0) return 1;
  if(power==1) return 2;
  int halfPower=fastExponent(base,power/2);
  if(power%2==0){
    return halfPower*halfPower;
  }else{
    return 2*halfPower*halfPower;
  }
}
int main(){
  int base,power;//base=2
  cin>>base>>power;
  cout<<exponent(base,power)<<endl;
  cout<<fastExponent(base,power);

}


```
