### Description
[387E](https://leetcode.com/problems/first-unique-character-in-a-string/description/)

### Solution

    public int firstUniqChar(String s) {
        int[] map = new int[26];
        char[] ch = s.toCharArray();
        for (char c : ch) {
            map[c - 'a']++;
        }
        for (int i = 0; i < ch.length; i++) {
            if (map[ch[i] - 'a'] == 1) return i;
        }
        return -1;
    }
    
