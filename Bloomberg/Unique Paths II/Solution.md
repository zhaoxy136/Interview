### Description
[63M](https://leetcode.com/problems/unique-paths-ii/description/)

### Solution

    class Solution {
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        if (obstacleGrid == null || obstacleGrid.length == 0) return 0;
        int[] dp = new int[obstacleGrid[0].length];
        for (int i = 0; i < obstacleGrid[0].length && obstacleGrid[0][i] == 0; i++) {
            dp[i] = 1;
        }
        for (int i = 1; i < obstacleGrid.length; i++) {
            dp[0] = obstacleGrid[i][0] == 1 ? 0 : dp[0];
            for (int j = 1; j < obstacleGrid[0].length; j++) {
                dp[j] = obstacleGrid[i][j] == 0 ? dp[j] + dp[j-1] : 0;
            }
        }
        return dp[obstacleGrid[0].length - 1];
    }
    }

### Similar
[Unique Paths](https://leetcode.com/problems/unique-paths/description/)
