## Longest Palindromic
```
using namespace std;
void findPalindromeString(int left, int right,vector<int> &currSubString,string str ){
  int currLeft=left;
  int currRight=right;
  while(currLeft>=0 && currRight<=str.length()-1 && str[currLeft]==str[currRight]){
      currLeft--;
      currRight++;
    }
  if(currLeft!=left){
     currSubString[0]=currLeft+1;
     currSubString[1]=currRight-1;
  }
   return;
}
void findMaxSubString(vector<int> &maxSubString,vector<int> &currSubString){
  int currMax=currSubString[1]-currSubString[0]+1;
  int strMax=maxSubString[1]-maxSubString[0]+1;
  if(currMax>strMax){
    maxSubString[0]=currSubString[0];
    maxSubString[1]=currSubString[1];
  }
  return;
}
string longestPalindromicSubstring(string str) {
   int n=str.length();
   vector<int> maxSubString={0,0};
   for(int i=1;i<n;i++){
     vector<int> currSubString={0,0};
     findPalindromeString(i-1,i+1,currSubString,str);
     findMaxSubString(maxSubString,currSubString);
     findPalindromeString(i-1,i,currSubString,str);
     findMaxSubString(maxSubString,currSubString);
   }
   string res="";
   for(int i=maxSubString[0];i<=maxSubString[1];i++){
     res+=str[i];
   }
   return res;
}

```

#### Complexity
- Time: O(n^2)
- Space : O(n)
