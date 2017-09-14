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
