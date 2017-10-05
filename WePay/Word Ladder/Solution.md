[LeetCode:127M](https://leetcode.com/problems/word-ladder/description/)

Solution:
//One Way BFS

    class Solution {
    public int ladderLength(String beginWord, String endWord, List<String> wordList) {
        Set<String> set = new HashSet<>(wordList);
        if (!set.contains(endWord)) {
            return 0;
        }
        Set<String> visited = new HashSet<>();
        Queue<String> queue = new LinkedList<>();
        queue.add(beginWord);
        visited.add(beginWord);
        int len = 1;
        while (!queue.isEmpty()) {
            int size = queue.size();
            while (size-- > 0) {
                String tmp = queue.poll();
                if (tmp.equals(endWord)) return len;
                List<String> ladder = getLadder(tmp);
                for (String s : ladder) {
                    if (set.contains(s) && !visited.contains(s)) {
                        queue.add(s);
                        visited.add(s);
                    }
                }
            }
            len++;
        }
        return 0;
    }
    
    public List<String> getLadder(String word) {
        char[] str = word.toCharArray();
        List<String> res = new ArrayList<>();
        for (int i = 0; i < str.length; i++) {
            char c = str[i];
            for (char j = 'a'; j <= 'z'; j++) {
                if (j == c) continue;
                str[i] = j;
                res.add(new String(str));
            }
            str[i] = c;
        }
        return res;
    }
    }

//Two Way BFS:

    class Solution {
    public int ladderLength(String beginWord, String endWord, List<String> wordList) {
        Set<String> words = new HashSet<>(wordList);
        if (!words.contains(endWord)) {
            return 0;
        }
        Set<String> beginSet = new HashSet<>();
        Set<String> endSet = new HashSet<>();
        Set<String> visited = new HashSet<>();
        
        beginSet.add(beginWord);
        endSet.add(endWord);
        visited.add(beginWord);
        visited.add(endWord);
        
        int len = 2;
        while (!beginSet.isEmpty() && !endSet.isEmpty()) {
            if (endSet.size() < beginSet.size()) {
                Set<String> tmp = endSet;
                endSet = beginSet;
                beginSet = tmp;
            }//beginSet is smaller
            Set<String> newSet = new HashSet<>();
            for (String str : beginSet) {
                char[] ch = str.toCharArray();
                for (int i = 0; i < ch.length; i++) {
                    char c = ch[i];
                    for (char j = 'a'; j<= 'z'; j++) {
                        if (j == c) continue;
                        ch[i] = j;
                        String next = new String(ch);
                        if (endSet.contains(next)) return len;
                        if (words.contains(next) && !visited.contains(next)) {
                            newSet.add(next);
                            visited.add(next);
                        }
                    }
                    ch[i] = c;
                }
            }
            beginSet = newSet;
            len++;
        }
        return 0;
    }
    }
    
