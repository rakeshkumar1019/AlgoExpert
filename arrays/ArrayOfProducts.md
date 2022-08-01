# Array Of Products
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/ArrayOfProducts.png?token=GHSAT0AAAAAABVRPMTCUUNYKTE2N7KI3354YW4CQZA)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/ArrayOfProducts.png?token=GHSAT0AAAAAABVRPMTCUUNYKTE2N7KI3354YW4CQZA)

#### Brute Force: Using Two Loops
Complexity:
- Time: O(n^2)
- Space: O(n)

#### Optimal Approch: Using Pre Computaion Method 
Note: for `product[i] = leftProduct[i-1]* rightProduct[i+1] `
Complexity:
- Time: O(n)
- Space: O(n)

```cpp
#include <vector>
using namespace std;
vector<int> arrayOfProducts(vector<int> array) {
 int n=array.size();
  if(n<=1) return array;
 vector<int> leftProduct(n,1);
 vector<int> rightProduct(n,1);
 vector<int> res;
 int currentProduct=1;
 for(int i=1;i<n;i++){
   currentProduct=array[i-1]*currentProduct;
   leftProduct[i]=currentProduct;
 }
 currentProduct=1;
 for(int i=n-2;i>=0;i--){
   currentProduct=array[i+1]*currentProduct;
   rightProduct[i]=currentProduct;
 }

for(int i=0;i<n;i++){
  res.push_back(leftProduct[i]*rightProduct[i]);
}
return res;
}

```
