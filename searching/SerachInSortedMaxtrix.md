T.C : O(n+m)

S.C : O(1)

```cpp
#include <vector>
using namespace std;

vector<int> searchInSortedMatrix(vector<vector<int>> matrix, int target) {
    int row=0;
    int col=matrix[0].size()-1;
    int n=matrix.size()-1;
    int m=0;
    vector<int>indexs;
    while(row<=n && col>=m){
      if(matrix[row][col]==target){
        indexs.push_back(row);
        indexs.push_back(col);
        return indexs;
      }else if(matrix[row][col]>target){
        col--;
      }else{
        row++;
      }
    }
  indexs.push_back(-1);
  indexs.push_back(-1);
  return indexs;
}

```
