```cpp
#include<bits/stdc++.h>
#include<iostream>
using namespace std;
void printSpelling(int n,string words[10]){
    if(n==0) return;
    int digit=n%10;
    int num=n/10;
    printSpelling(num,words);
    cout<<words[digit];
}
int main(){
  int n;
  cin>>n;
  string words[10]={"zero","one","two","three","four","five","six","seven","eight","nine"};
  printSpelling(n,words);
}

```
