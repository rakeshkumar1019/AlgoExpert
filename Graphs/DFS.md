Question Link: https://practice.geeksforgeeks.org/problems/depth-first-traversal-for-a-graph/1

Expected Time Complexity: O(V + E)
Expected Auxiliary Space: O(V)

```cpp
class Solution {
  public:
    void dfsHelper(vector<int> adj[] , int s ,vector<bool> &visited,vector<int>&res){
     visited[s]=true;
     res.push_back(s);
     for(auto i : adj[s]){
         if(!visited[i]){
           dfsHelper(adj,i,visited,res);  
         }
     }
     return;
    }
    // Function to return a list containing the DFS traversal of the graph.
    vector<int> dfsOfGraph(int V, vector<int> adj[]) {
        int N = V;
        vector<int> res;
        vector<bool> visited(N,false);
        dfsHelper(adj,0,visited,res);
        return res;
    }
};
```
