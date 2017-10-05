[LeetCode:36M](https://leetcode.com/problems/valid-sudoku/description/)

Solution:
    
    class Solution {
    public boolean isValidSudoku(char[][] board) {
        boolean[][] used1 = new boolean[9][9];//used to check each row
        boolean[][] used2 = new boolean[9][9];//used to check each column
        boolean[][] used3 = new boolean[9][9];//used to check each subbox
        for (int i = 0; i < 9; i++) {
            for (int j = 0; j < 9; j++) {
                if (board[i][j] == '.') {
                    int num = board[i][j] - '0';
                    int index = (i / 3) * 3 + (j / 3);
                    if (used1[i][num-1] || used2[j][num-1] || used3[index][num-1]) {
                        return false;
                    }
                    used1[i][num-1] = true;
                    used2[j][num-1] = true;
                    used3[index][num-1] = true;
                }
            }
        }
        return true;
    }
    }
