```cpp
using namespace std;

bool generateDocument(string characters, string document) {
  int n=characters.length();
  int l=document.length();
  if(n<=0 || l<=0) return true;
  map<char,int> m;
  for(int i=0;i<n;i++){
    if(m.find(characters[i])!=m.end()){
      m[characters[i]]+=1;
    }else{
      m[characters[i]]=1;
    }
  }

  for(int i=0;i<l;i++){
    if(m[document[i]]>0){
      m[document[i]]-=1;
    }else{
      return false;
    }
  }
  return true;
}

```
