Algorithm:
1. Use a boolean list to mark all the vertices as not visited.
2. Initially mark first vertex as visited(true).
3. Create a queue for BFS and push first vertex in queue.
4. While queue is not empty:
   I. Keep adding front element in output list and popping it from queue.
   II. Traverse over all the connected components of front element.
   III. If they aren't visited, mark them visited and add to queue.
5. Return the output list.

>Complexity:
>>Time Complexity: O(V + E)
>>
>>Space Complexity: O(V)

```cpp
#include<bits/stdc++.h>
using namespace std;
void addEdges(vector<int> adj[] , int u ,int v,bool isDirected){
    adj[u].push_back(v);
    if(!isDirected){
      adj[v].push_back(u);
    }
}

void printAdj(vector<int> adj[],int N){
  for(int i=0;i<N;i++){
    cout<<i<<":";
    for(auto it = adj[i].begin();it!=adj[i].end();it++){
           cout<<*it<<" ";
    }cout<<endl;
  }
}

void bfsHelper(vector<int>adj[],vector<bool> &isVisited,int s){
   queue<int> q;
   q.push(s);
   isVisited[s]=true;
   while(!q.empty()){
     int front = q.front();
     q.pop();
     cout<<front<<" ";
     for(auto j:adj[front]){
       if(!isVisited[j]){
         q.push(j);
         isVisited[j]=true;
       }
     }
   }
   return;
}

void bfs(vector<int>adj[],int N){
   vector<bool> isVisited(N,false);
   for(int i=0;i<N;i++){
     if(!isVisited[i]){
      bfsHelper(adj,isVisited,i);
     }
   }
}


int main(){
  int N,V;
  cin>>N>>V;
  vector<int> adj[N];
  for(int i=0;i<V;i++){
    int u,v;
    cin>>u>>v;
    addEdges(adj,u,v,false);
  }
  printAdj(adj,N);
  bfs(adj,N);
  
}

```
