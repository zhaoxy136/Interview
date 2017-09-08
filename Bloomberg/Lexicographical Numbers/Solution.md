### Description
[386M](https://leetcode.com/problems/lexicographical-numbers/description/)

### Solution

    public List<Integer> lexicalOrder(int n) {
        List<Integer> res = new ArrayList<>();
        if (n < 1) return res;
        int cur = 1;
        for (int i = 0; i < n; i++) {
            res.add(cur);
            if (cur * 10 <= n) {
                cur = cur * 10;
            } else {
                while (cur == n || cur % 10 == 9) {
                    cur = cur / 10;
                }
                cur++;
            }
        }
        return res;
    }
