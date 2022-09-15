Question Link: 
1.https://www.codingninjas.com/codestudio/problems/rod-cutting-problem_800284?leftPanelTab=1
2.https://www.geeksforgeeks.org/cutting-a-rod-dp-13/

Video Link: https://www.youtube.com/watch?v=SZqAQLjDsag&list=PL_z_8CaSLPWekqhdCPmFohncHwz8TY2Go&index=14

Complexity : Time | space --> O(n*w) 

```cpp
int unboundedKapsack(vector<int> &price,vector<int> &length,int n,int W){
    vector<vector<int> >res(n+1,vector<int>(W+1,0));
    for(int j=0;j<=W;j++){
        res[0][j]= 0;
    }
    for(int i=0;i<=n;i++){
        res[i][0]=0;
    }
    for(int i=1;i<=n;i++){
        for(int j=1;j<=W;j++){
            if(length[i-1] <= j){
                res[i][j] = max(price[i-1]+res[i][j-length[i-1]],res[i-1][j]);
            }else{
                res[i][j] = res[i-1][j];
            }
        }
    }
    return res[n][W];
}
int cutRod(vector<int> &price, int n)
{
	vector<int> length;
    for(int i=1;i<=n;i++){
        length.push_back(i);
    }
    return unboundedKapsack(price,length,n,n); 
}

```
