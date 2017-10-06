[LeetCode: 126H](https://leetcode.com/problems/word-ladder-ii/description/)


Solution:

    class Solution {
    public List<List<String>> findLadders(String beginWord, String endWord, List<String> wordList) {
        List<List<String>> res = new ArrayList<>();
        Set<String> dict = new HashSet<>(wordList);
        if (!dict.contains(endWord)) return res;
        
        Map<String, Integer> distance = new HashMap<>();
        Map<String, List<String>> neighbors = new HashMap<>();
        if (!getLadders(neighbors, distance, dict, beginWord, endWord)) return res;
        getPaths(res, new ArrayList<>(), neighbors, distance, beginWord, endWord);
        return res;
    }
    
    public boolean getLadders(Map<String, List<String>> neighbors, Map<String, Integer> distance, Set<String> dict,
                      String beginWord, String endWord) {
        Queue<String> queue = new LinkedList<>();
        distance.put(beginWord, 0);
        queue.add(beginWord);
        int len = 1;
        while (!queue.isEmpty()) {
            int size = queue.size();
            while (size-- > 0) {
                String tmp = queue.poll();
                if (tmp.equals(endWord)) return true;
                neighbors.put(tmp, new ArrayList<>());
                char[] str = tmp.toCharArray();
                for (int i = 0; i < str.length; i++) {
                    char ch = str[i];
                    for (char j = 'a'; j <= 'z'; j++) {
                        if (j == ch) continue;
                        str[i] = j;
                        String next = String.valueOf(str);
                        if (dict.contains(next)) {
                            neighbors.get(tmp).add(next);
                            if (!distance.containsKey(next)) {
                                distance.put(next, len);
                                queue.add(next);
                            }
                        }
                    }
                    str[i] = ch;
                }
            }
            len++;
        }
        return false;
    }
    
    public void getPaths(List<List<String>> res, List<String> list, Map<String, List<String>> neighbors, 
                    Map<String, Integer> distance, String beginWord, String endWord) {
        list.add(beginWord);
        if (beginWord.equals(endWord)) {
            res.add(new ArrayList<>(list));
        } else if (neighbors.containsKey(beginWord)) {
            for (String neighbor : neighbors.get(beginWord)) {
                if (distance.get(neighbor) == distance.get(beginWord) + 1)
                    getPaths(res, list, neighbors, distance, neighbor, endWord);
            }
        }
        list.remove(list.size() - 1);
    }
    }
    
Follow-up: just return one valid path
//Map stores Entry<nextStep, prevStep>

    class Solution {
    public List<List<String>> findLadders(String beginWord, String endWord, List<String> wordList) {
        List<String> res = new ArrayList<>();
        Set<String> dict = new HashSet<>(wordList);
        if (!dict.contains(endWord)) return res;
        
        Map<String, String> neighbors = new HashMap<>();
        if (!getLadders(neighbors, dict, beginWord, endWord)) return res;
        
        String cur = endWord;
        while (!cur.equals(beginWord)) {
            res.add(0, cur);
            cur = neighbors.get(cur);
        }
        res.add(0, cur);
        return res;
    }
    public boolean getLadders(Map<String, String> neighbors, Set<String> dict, String beginWord, String endWord) {
        Queue<String> queue = new LinkedList<>();
        queue.add(beginWord);
        while (!queue.isEmpty()) {
            int size = queue.size();
            while (size-- > 0) {
                String tmp = queue.poll();
                if (tmp.equals(endWord)) return true;
                char[] str = tmp.toCharArray();
                for (int i = 0; i < str.length; i++) {
                    char ch = str[i];
                    for (char j = 'a'; j <= 'z'; j++) {
                        if (j == ch) continue;
                        str[i] = j;
                        String next = String.valueOf(str);
                        if (dict.contains(next) && !map.containsKey(next)) {
                            map.put(next, tmp);
                            queue.add(next);
                        }
                    }
                    str[i] = ch;
                }
            }
        }
        return false;
    }
    }
