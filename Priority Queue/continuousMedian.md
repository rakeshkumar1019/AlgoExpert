T.C: O(logn)

S.C: O(n)

```cpp

#include<queue>
using namespace std;

// Do not edit the class below except for
// the insert method. Feel free to add new
// properties and methods to the class.
class ContinuousMedianHandler {
public:
  double median;
  priority_queue<double> maxHeap; 
  priority_queue<double,vector<double>,greater<double>>minHeap;
  int signum(int a ,int b){
    if(a==b){
      return 0;
    }else if(a>b){
      return 1;
    }else{
      return -1;
    }
  }
  void insert(int number) {
    switch(signum(maxHeap.size(),minHeap.size())){
      
      case 0: if(number>median){
          minHeap.push(number);
          median=minHeap.top();
        }else{
          maxHeap.push(number);
          median=maxHeap.top();
        }
      break;
    
      case 1: if(number>median){
            minHeap.push(number);
            median =(minHeap.top()+maxHeap.top())/2;
                 
          }else{
            minHeap.push(maxHeap.top());
            maxHeap.pop();
            maxHeap.push(number);
            median =(minHeap.top()+maxHeap.top())/2;
                 
          }
        break;
      
      case -1: if(number>median){
               maxHeap.push(minHeap.top());
               minHeap.pop();
               minHeap.push(number);
              median =(minHeap.top()+maxHeap.top())/2;
               
             }else{
               maxHeap.push(number);
               median=maxHeap.top();
             }
           break;
    }    
  }

  double getMedian() { return median; }
};

```
