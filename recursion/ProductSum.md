# Product Sum
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/ProductSum.png)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/ProductSum.png)

#### Complexity:
>O(n) time | O(d) space - where n is the total number of elements in the array, including sub-elements, and d is the greatest depth of "special" arrays in the array

##### Hint1:
>Try using recursion to solve this problem.

##### Hint2:
>Initialize the product sum of the "special" array to 0. Then, iterate through all of the array's elements; if you come across a number, add it to the product sum; if you come across another "special" array, recursively call the productSum function on it and add the returned value to the product sum. How will you handle multiplying the product sums at a given level of depth?

##### Hint3:
>Have the productSum function take in a second parameter: the multiplier, initialized to 1. Whenever you recursively call the productSum function, pass in the multiplier incremented by 1.

```cpp
#include <any>
#include <vector>

using namespace std;

// Tip: You can use el.type() == typeid(vector<any>) to check whether an item is
// a list or an integer.
// If you know an element of the array is vector<any> you can cast it using:
//     any_cast<vector<any>>(element)
// If you know an element of the array is an int you can cast it using:
//     any_cast<int>(element)
int productSumHelper(vector<any> array, int level){
  int productSum=0;
  for(any currElem: array){
    if(currElem.type()==typeid(int)){
      productSum+=any_cast<int>(currElem)*level;
    }
    else if(currElem.type()==typeid(vector<any>)){
      productSum+=level*productSumHelper(any_cast<vector<any>>(currElem),level+1);
    }
  }
  return productSum;
}
int productSum(vector<any> array) {
   int level=1;
   return productSumHelper(array,level);
}

```
