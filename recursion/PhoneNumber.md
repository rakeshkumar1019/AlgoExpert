## Phone Number Mnemonics

```
#include <vector>
using namespace std;
vector<string> mapping={"0","1","abc","def","ghi","jkl","mno","pqrs","tuv","wxyz"};
void solvePhoneNumberMnemonics(string phoneNumber,int idx,string currOutputStr,vector<string> &Mnemonics ){
  if(idx==phoneNumber.length()){
    Mnemonics.push_back(currOutputStr);
    return;
  }

  int number=phoneNumber[idx]-'0'; // convert char to number ex: '2'-'0'=2 (dealing with ascii values here)
  string keyLetter=mapping[number];
  for(int i=0;i<keyLetter.length();i++){
    currOutputStr.push_back(keyLetter[i]);
    solvePhoneNumberMnemonics(phoneNumber,idx+1,currOutputStr,Mnemonics);
    currOutputStr.pop_back();
  }
}
vector<string> phoneNumberMnemonics(string phoneNumber) {
  vector<string> Mnemonics;
  if(phoneNumber.length()==0) return Mnemonics;
  string currOutputStr="";
  solvePhoneNumberMnemonics(phoneNumber,0,currOutputStr,Mnemonics);
  return Mnemonics;
}

```

#### Complexity:

>O(4^n * n) time | O(4^n * n) space - where n is the length of the phone number
