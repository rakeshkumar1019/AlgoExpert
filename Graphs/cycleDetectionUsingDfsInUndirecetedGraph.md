Complexity: 
- Time: O(N+E)
- Space: O(N+E) + O(N) +O(N)

>N for visiting N node and E for traversing all the adjacent nodes overall, space for adjacency list, vsisited array & auxiliary space. 


```cpp
#include<iostream>
#include<bits/stdc++.h>
using namespace std;
void addEdges(vector<int> adj[],int u,int v,bool isDirected){
  adj[u].push_back(v);
  if(!isDirected){
    adj[v].push_back(u);
  }
}

void printAdj(vector<int> adj[],int N){
     for(int i=0;i<=N;i++){
       cout<<i<<":"<<" ";
       for(auto it = adj[i].begin();it!=adj[i].end();it++){
         cout<<*it<<" ";
       }cout<<endl;
     }
}
bool isdfsCycle(vector<int> adj[],vector<bool> &visited,int parent,int s){
    visited[s] = true;
    for(auto it : adj[s]){
      if(!visited[it]){
        if(isdfsCycle(adj,visited,s,it)){
          return true;
        }
      }else{
        if(it != parent){
          return true;
        }
      }
    }
}

bool dfsCycle(vector<int> adj[],int N){
  vector<bool> visited(N+1,false);
  for(int i=1;i<=N;i++){
    if(!visited[i]){
      if(isdfsCycle(adj,visited,-1,i)){
        return true;
      }
    }
  }
  return false;
}

int main(){
  int N,V;
  cin>>N>>V;
  vector<int> adj[N+1];
  for(int i=0;i<V;i++){
    int u,v;
    cin>>u>>v;
    addEdges(adj,u,v,false);
  }
  printAdj(adj,N);
  cout<<dfsCycle(adj,N)<<endl;

}

```
