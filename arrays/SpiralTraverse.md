# Spiral Traverse
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/SpiralTraverse.png?token=GHSAT0AAAAAABVRPMTCGCX6DQ3AXBG4C3CKYW4CLRQ)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/SpiralTraverse.png?token=GHSAT0AAAAAABVRPMTCGCX6DQ3AXBG4C3CKYW4CLRQ)

Complexity:
- Time: O(n^2)
- Space: O(n)

#### Note: Use Direction pointers
```cpp
using namespace std;

vector<int> spiralTraverse(vector<vector<int>> array) {
   int n=array.size();
   int m=array[0].size(); 
   vector<int> res;
   int dir=0;
   int left=0;
   int right=m-1;
   int top=0;
   int bottom=n-1; 
  //all 4 pointers should not go out of bounding after creating new boundaries 
   while(top<=bottom && left<=right){
     if(dir==0){
       for(int i=left;i<=right;i++){
         res.push_back(array[top][i]);
       }
       top++;
     }
     if(dir==1){
       for(int i=top;i<=bottom;i++){
         res.push_back(array[i][right]);
       }
       right--;
     }
     if(dir==2){
       for(int i=right;i>=left;i--){
         res.push_back(array[bottom][i]);
       }
       bottom--;
     }
     if(dir==3){
       for(int i=bottom;i>=top;i--){
         res.push_back(array[i][left]);
       }
       left++;
     }
     dir++;
     dir=dir%4;
   }
   return res; 
}

```
