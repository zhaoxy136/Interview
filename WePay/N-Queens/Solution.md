[LeetCode: 51H](https://leetcode.com/problems/n-queens/description/)

Solution:

    class Solution {
    public List<List<String>> solveNQueens(int n) {
        List<List<String>> res = new ArrayList<>();
        helper(res, new ArrayList<>(), n);
        return res;
    }
    public void helper(List<List<String>> res, List<Integer> list, int n) {
        if (list.size() == n) {
            List<String> sol = new ArrayList<>();
            char[] ch = new char[n];
            Arrays.fill(ch, '.');
            for (int i : list) {
                ch[i] = 'Q';
                sol.add(new String(ch));
                ch[i] = '.';
            }
            res.add(sol);
            return;
        }
        for (int i = 0; i < n; i++) {
            if (isValid(list, i)) {
                list.add(i);
                helper(res, list, n);
                list.remove(list.size() - 1);
            }
        }
    }
    
    public boolean isValid(List<Integer> list, int col) {
        int row = list.size();
        for (int i = 0; i < row; i++) {
            int j = list.get(i);
            if (j == col || i - j == row - col || i + j == row + col) return false;
        }
        return true;
    }
    }
    
Follow-Up: nstead outputting board configurations, return the total number of distinct solutions.

    class Solution {
    public int totalNQueens(int n) {
        return helper(new ArrayList<>(), n);
    }
    
    public int helper(List<Integer> list, int n) {
        if (list.size() == n) {
            return 1;
        }
        int count = 0;
        for (int i = 0; i < n; i++) {
            if (isValid(list, i)) {
                list.add(i);
                count += helper(list, n);
                list.remove(list.size() - 1);
            }
        }
        return count;
    }
    
    public boolean isValid(List<Integer> list, int col) {
        int row = list.size();
        for (int i = 0; i < row; i++) {
            int j = list.get(i);
            if (j == col || i - j == row - col || i + j == row + col) return false;
        }
        return true;
    }
    }
    
    
