![](/assets/Screen Shot 2018-01-15 at 2.02.08 PM.png)
![](/assets/Screen Shot 2018-01-15 at 2.02.53 PM.png)
#Idea
##DFS
1. To count the area of each island using dfs(**helper function**).
2. During the dfs, set the value of each point in the visited island to 0.

#Solution
##code
```
public int maxAreaOfIsland(int[][] grid){
    // result
    int max_area = 0;
    // traverse the grid to find the island with the max_area
    for(int i = 0; i < grid.length; i++){
        for(int j = 0; j < grid[0].length; j++){
            //use a helper function to count the area of the island
            //encounter a island, compare its area with max_area
            if(grid[i][j] == 1) max_area = Math.max(max_area, helper(grid, i, j));
        }
    }
    return max_area;
}

public int helper(int[][] grid, int i , int j){
    if(i >= 0 && i < grid.length && j >= 0 && j < grid[0].length && grid[i][j] == 1){
        // set the visited point to 0
        grid[i][j] = 0;
        // island area = 4 direction 1
        return 1 + helper(grid, i-1, j) + helper(grid, i+1, j) + helper(grid, i, j-1) + helper(grid, i, j+1);
    }
    return 0;
}

```