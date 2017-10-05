[LeetCode: 54M](https://leetcode.com/problems/spiral-matrix/description/)

Solution:

    class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> list = new ArrayList<>();
        if (matrix == null || matrix.length == 0) return list;
        helper(list, matrix, 0, matrix.length - 1, 0, matrix[0].length - 1);
        return list;
    }
    
    public void helper(List<Integer> list, int[][] matrix, int r1, int r2, int c1, int c2) {
        if (r1 > r2 || c1 > c2) return;
        for (int i = c1; i <= c2; i++) {
            list.add(matrix[r1][i]);
        }
        for (int i = r1 + 1; i <= r2; i++) {
            list.add(matrix[i][c2]);
        }
        if (r1 < r2 && c1 < c2) {
            for (int i = c2 - 1; i >= c1; i--) {
                list.add(matrix[r2][i]);
            }
            for (int i = r2 - 1; i > r1; i--) {
                list.add(matrix[i][c1]);
            }
        }
        helper(list, matrix, r1 + 1, r2 - 1, c1 + 1, c2 - 1);
    }
    }
