# Tournament Winner
[![](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/tournamentWinner.png)](https://raw.githubusercontent.com/rakeshkumar1019/AlgoExpert/main/images/tournamentWinner.png)

#### Optimal Approch :  Using Map
Complexity:
- Time : O(n)
- Space : O(k)

```cpp
#include <vector>
#include<map>
#include<iterator>
using namespace std;
void storePoints(map<string,int> &points, string algo){
  if(points.find(algo)!=points.end()){
    points[algo]+=3;
    return;
  }
  points[algo]=3;
  return;
}
string tournamentWinner(vector<vector<string>> competitions, vector<int> results){
  int n=competitions.size();
  if(n<=0) return " ";
  int m=competitions[0].size();
  map<string,int> points;
  for(int i=0;i<n;i++){
    if(results[i]==1){
      storePoints(points,competitions[i][0]);
    }
    if(results[i]==0){
      storePoints(points,competitions[i][1]);
    }
  }
  string res;
  int maxPoint=0;
  map<string,int>:: iterator it;
  for(it=points.begin();it!=points.end();it++){
      if(it->second > maxPoint){
        maxPoint=it->second;
        res=it->first;
      } 
  }
  return res;
}

```
