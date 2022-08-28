Question Lin: https://www.codingninjas.com/codestudio/problems/aggressive-cows_1082559?leftPanelTab=1

T.C : O(Nlogn)

S.C : O(1)

```cpp
bool isPossible(vector<int> stalls, int k,int minDist){
    int noOfCows=1;
    int previousDist=stalls[0];
    for(int i=1;i<stalls.size();i++){
        if(stalls[i]-previousDist>= minDist){
            noOfCows++;
            previousDist=stalls[i];
            if(noOfCows >= k){   
                return true;
            }
        }
    }
    return false;
}

int aggressiveCows(vector<int> &stalls, int k)
{
    sort(stalls.begin(),stalls.end());
    int left=0;
    int right=0;
    for(int i=0;i<stalls.size();i++){
        right=max(right,stalls[i]);
    }
    int res=-1;
    while(left<=right){
        int mid=left+(right-left)/2;
        if(isPossible(stalls,k,mid)){
            res=mid;
            left=mid+1;
        }else{
            right=mid-1;
        }
    }
    return res;
    
}
```
