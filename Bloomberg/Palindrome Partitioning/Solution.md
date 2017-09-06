### Description
[113M](https://leetcode.com/problems/palindrome-partitioning/description/)

### Solution

    class Solution {
    public List<List<String>> partition(String s) {
        if (s == null || s.length() == 0) {
            return new ArrayList<>();
        }
        boolean[][] isPalindrome = new boolean[s.length()][s.length()];
        for (int k = 0; k < s.length(); k++) {
            for (int i = 0; i + k < s.length(); i++) {
                if (s.charAt(i) == s.charAt(i+k) && (k <= 1 || isPalindrome[i+1][i+k-1])) {
                    isPalindrome[i][i+k] = true;
                }
            }
        }
        List<List<String>> res = new ArrayList<>();
        helper(res, new ArrayList<String>(), s, 0, isPalindrome);
        return res;
    }
    
    public void helper(List<List<String>> res, List<String> list, String s, int start, boolean[][] isPalindrome) {
        if (start == s.length()) {
            res.add(new ArrayList<>(list));
            return;
        }
        for (int end = start; end < s.length(); end++) {
            if (isPalindrome[start][end]) {
                list.add(s.substring(start, end+1));
                helper(res, list, s, end+1, isPalindrome);
                list.remove(list.size() - 1);
            }
        }
    }
    }

### Similar Problem
[140H](https://leetcode.com/problems/word-break-ii/description/)
