### Description
[140H](https://leetcode.com/problems/word-break-ii/description/)

### Solution
//Version 0:

    public class Solution {
    public List<String> wordBreak(String s, List<String> wordDict) {
        return helper(s, wordDict, new HashMap<Integer, List<String>>(), 0);
    }
    private List<String> helper(String s, List<String> wordDict, Map<Integer, List<String>> map, int start) {
        if (map.containsKey(start)) {
            return map.get(start);
        }
        List<String> res = new ArrayList<>();
        if (start == s.length()) {
            res.add("");
            return res;
        }
        for (int end = start + 1; end <= s.length(); end++) {
            String str = s.substring(start, end);
            if (wordDict.contains(str)) {
                List<String> list = helper(s, wordDict, map, end);
                for (String l : list) {
                    res.add(str + (l.equals("") ? "" : " ") + l);
                }
            }
        }
        map.put(start, res);
        return res;
    }
    }
    
//Version 1: as the length of s could become larger and larger, but the size of wordDict won't be too big

    public class Solution {
    public List<String> wordBreak(String s, List<String> wordDict) {
        return helper(s, wordDict, new HashMap<String, List<String>>());
    }
    private List<String> helper(String s, List<String> wordDict, Map<String, List<String>> map) {
        if (map.containsKey(s)) {
            return map.get(s);
        }
        List<String> res = new ArrayList<>();
        if (s.equals("")) {
            res.add("");
            return res;
        }
        for (String word : wordDict) {
            if (s.startsWith(word)) {
                List<String> list = helper(s.substring(word.length()), wordDict, map);
                for (String l : list) {
                    res.add(word + (l.equals("") ? "" : " ") + l);
                }
            }
        }
        map.put(s, res);
        return res;
    }
    }
