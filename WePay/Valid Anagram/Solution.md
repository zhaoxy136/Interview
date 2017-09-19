### Description
[242E](https://leetcode.com/problems/valid-anagram/description/)

### Solution

    public class Solution {
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) return false;
        int[] sletters = new int[26];
        int[] tletters = new int[26];
        for (int i = 0; i < s.length(); i++) {
            sletters[s.charAt(i) - 'a']++;
        }
        for (int i = 0; i < t.length(); i++) {
            tletters[t.charAt(i) - 'a']++;
        }
        return Arrays.equals(sletters, tletters);
    }
    }
