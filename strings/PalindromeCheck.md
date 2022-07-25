# Palindrome Check
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/PalindromeCheck.png)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/PalindromeCheck.png)

#### Complexity:
- Time : O(n)
- Space : O(1)

```cpp
using namespace std;

bool isPalindrome(string str) {
  int n=str.length();
  int left=0;
  int right=n-1;
  while(left<right){
    if(str[left]==str[right]){
      left++;
      right--;
    }else{
      return false;
    }
  }
  return true;
}

```
