```cpp
using namespace std;

string runLengthEncoding(string str) {
  int n=str.length();
  if(n<=0) return str;
  int count=1;
  char currentChar=str[0];
  string enCodedStr="";
  for(int i=1;i<n;i++){
    if(str[i]==currentChar){
      count++;
    }else{
      int noOfLoop=count/9;
      int remainingNumber=(count-(noOfLoop*9))%9;
      for(int j=1;j<=noOfLoop;j++){
        enCodedStr=enCodedStr+"9"+currentChar;
      }
     if(remainingNumber>0) enCodedStr=enCodedStr+to_string(remainingNumber)+currentChar;
      currentChar=str[i];
      count=1;
    }
  }

  int noOfLoop=count/9;
  int remainingNumber=(count-(noOfLoop*9))%9;
  for(int j=1;j<=noOfLoop;j++){
    enCodedStr=enCodedStr+"9"+currentChar;
  }
  if(remainingNumber>0) enCodedStr=enCodedStr+to_string(remainingNumber)+currentChar;
  
  return enCodedStr;
}

```
