### Description
[50M](https://leetcode.com/problems/powx-n/description/)

### Solution

    class Solution {
    public double myPow(double x, int n) {
        if (n == 0) return 1;
        if (n < 0) {
            //handle n = Integer.MIN_VALUE
            n = -1 * (n + 1);
            return 1 / (x * myPow(x, n));
        }
        if (n % 2 == 0) {
            return myPow(x * x, n / 2);
        }
        return x * myPow(x, n - 1);
    }
    }
