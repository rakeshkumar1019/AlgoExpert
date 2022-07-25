# Caesar Cipher Encryptor
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/CaeserCipherEncrypter.png)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/CaeserCipherEncrypter.png)

Complexity:
- Time : O(n)
- Space : O(n)

```cpp
using namespace std;

string caesarCypherEncryptor(string str, int key) {
  string solution="";
  for(int i=0;i<str.length();i++){
    int diff=str[i]-'a';
    int cypher=(diff+key)%26+'a';
    char encrypt= cypher;
    solution+=encrypt;
  }
  return solution;
}

```
