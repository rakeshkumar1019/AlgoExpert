```cpp
using namespace std;

int firstNonRepeatingCharacter(string string) {
  int n=string.length();
  if(n<=0) return -1;
  if(n==1) return 0;
  map<char,int>m;
  for(int i=0;i<n;i++){
    if(m.find(string[i])!=m.end()){
      m[string[i]]+=1;
    }else{
      m[string[i]]=1;
    }
  }

  for(int i=0;i<n;i++){
    if(m[string[i]]==1){
      return i;
    }
  }
  return -1;
}

```
