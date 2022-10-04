Question link: https://practice.geeksforgeeks.org/problems/depth-first-traversal-for-a-graph/1

Time Complexity: O(V + E)

Auxiliary Space: O(V)

```cpp
#include<bits/stdc++.h>
using namespace std;
void addEdges(vector<int> adj[],int u,int v,bool isDirected){
   adj[u].push_back(v);
   if(!isDirected){
     adj[v].push_back(u);
   }
}
void dfsHelper(vector<int> adj[],int s,vector<bool> &visited){
     visited[s] =true;
     cout<<s<<" ";
     for(auto i : adj[s]){
       if(!visited[i]){
           dfsHelper(adj,i,visited);
       }
     }
}
void dfs(vector<int> adj[],int N){
  vector<bool>visited(N,false);
  dfsHelper(adj,2,visited);
  for(int i=0;i<N;i++){
    if(!visited[i]){
     dfsHelper(adj,i,visited);
    } 
  }
   return;
}
int main(){
  int N,V;
  cin>>N>>V;
  vector<int> adj[N];
  for(int i=0;i<V;i++){
    int u,v;
    cin>>u>>v;
    addEdges(adj,u,v,true);
  }
  dfs(adj,N);
}

```
