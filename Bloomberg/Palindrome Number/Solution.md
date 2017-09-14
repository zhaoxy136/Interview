### Description
[9E](https://leetcode.com/problems/palindrome-number/description/)

### Solution

    public boolean isPalindrome(int x) {
        if (x < 0 || x > 0 && x % 10 == 0) return false;
        int res = 0;
        while (res < x) {
            res = res * 10 + x % 10;
            x /= 10;
        }
        return res == x || res/10 == x;
    }

### Similar
[Reverse Integer: 7E](https://leetcode.com/problems/reverse-integer/description/)

    public int reverse(int x) {
        if (x < 0) return x == Integer.MIN_VALUE ? 0 : -1 * reverse(-x);
        int res = 0;
        while (x != 0) {
            int next = x % 10;
            if (res > Integer.MAX_VALUE / 10 || res == Integer.MAX_VALUE / 10 && next > 7) {
                return 0;
            }
            res = res * 10 + next;
            x = x / 10;
        }
        return res;
    }
