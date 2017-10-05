[LeetCode: 311M](https://leetcode.com/problems/sparse-matrix-multiplication/description/)

Solution:
//Version 0:

    class Solution {
    public int[][] multiply(int[][] A, int[][] B) {
        if (A == null || A.length == 0 || B == null || B.length == 0) return new int[0][0];
        if (A[0].length != B.length) {
            return new int[0][0];
        }
        int[][] res = new int[A.length][B[0].length];
        //A[0].length shoule be equal to B.length
        //A[i][j] * B[j][k] has contribution to res[i][k]
        for (int i = 0; i < A.length; i++) {
            for (int j = 0; j < A[0].length; j++) {
                if (A[i][j] == 0) continue;
                for (int k = 0; k < B[0].length; k++) {
                    res[i][k] += A[i][j] * B[j][k];
                }
            }
        }
        return res;
    }
    }


