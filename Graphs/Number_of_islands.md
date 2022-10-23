Question Link: https://leetcode.com/problems/number-of-islands/

Complexity:
- time: (N*M)
- space: O(1) + stack


```cpp
class Solution {
public:
    void bfs( vector<vector<char>>& grid, int i, int j, int row, int col ) {
        
        if ( i < 0 || i >= row || j < 0 || j >= col || grid[i][j] != '1' ){
            return;
        }
        grid[i][j] = '2';
        
        //      up     left   down  right  
        int dir_row[4] = { -1, 0, 1, 0 };
        int dir_col[4] = { 0 , -1, 0, 1 };
        
        
        for( int k = 0; k < 4; ++k ){
            bfs(grid, i+dir_row[k], j+dir_col[k], row, col );
        }
        
    }
    int numIslands(vector<vector<char>>& grid) {
        int row = grid.size();
        if( row == 0 ) return 0;
        int col = grid[0].size();
        
        int no_of_islands = 0;
        
        for( int i = 0; i < row; ++i ){
            for ( int j = 0; j < col; ++j ) {
                 if( grid[i][j] == '1' ){
                     bfs( grid, i, j, row, col );
                     no_of_islands++;
                 }
            }
        }
        return no_of_islands;
    }
};
```
