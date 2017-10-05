[LeetCode: 59M](https://leetcode.com/problems/spiral-matrix-ii/description/)

Solution:

    class Solution {
    public int[][] generateMatrix(int n) {
        int[][] res = new int[n][n];
        int row = 0, col = 0;
        int k = 0;
        int l = 1;
        int[] dir = {0, 1, 0, -1, 0};
        for (int i = 1; i <= n * n; i++) {
            res[row][col] = i;
            int x = row + dir[k];
            int y = col + dir[k+1];
            if (x < 0 || x >= n || y < 0 || y >= n || res[x][y] != 0) {
                row += dir[l];
                col += dir[l+1];
                if (l++ == 3) l = 0;
                if (k++ == 3) k = 0;
            } else {
                row = x;
                col = y;
            }
        }
        return res;
    }
    }
