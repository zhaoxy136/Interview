### Description
[3M](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)

### Solution

    public int lengthOfLongestSubstring(String s) {
        int[] map = new int[128];
        int res = 0;
        int start = 0, end = 0;
        while (end < s.length()) {
            char ch = s.charAt(end++);
            map[ch]++;
            while (map[ch] > 1) {
                char c = s.charAt(start++);
                map[c]--;
            }
            res = Math.max(res, end - start);
        }
        return res;
    }
