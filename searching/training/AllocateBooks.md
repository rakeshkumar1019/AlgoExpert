Question Link: https://www.interviewbit.com/problems/allocate-books/

T.C : O(nlogn)
S.C : O(1)


```cpp
bool isPossible(vector<int> A,int B,int mid){
    int numberOfStudents=1;
    int pages=0;
    for(int i=0;i<A.size();i++){
        if(pages+A[i]<=mid){
            pages+=A[i];
        }else{
            numberOfStudents++;
            if(numberOfStudents > B || A[i] > mid){
                return false;
            }
            pages=A[i];
        }
    }
    return true;
}

int Solution::books(vector<int> &A, int B) {
    int left=0;
    int right=0;
    if(B > A.size()){
        return -1;
    }
    for(int i=0;i<A.size();i++){
        right+=A[i];
    }
    
    int res=-1;
    while(left<=right){
        int mid=left+(right-left)/2;
        if(isPossible(A,B,mid)){
            res=mid;
            right=mid-1;
        }else{
            left=mid+1;
        }
    }
    return res;
}

```
