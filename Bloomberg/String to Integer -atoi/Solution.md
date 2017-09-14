### Description
[8M](https://leetcode.com/problems/string-to-integer-atoi/description/)

### Solution

    public int myAtoi(String str) {
        int i = 0;
        while (i < str.length() && str.charAt(i) == ' ') i++;
        if (i >= str.length()) return 0;
        int sign = 1;
        if (str.charAt(i) == '+' || str.charAt(i) =='-') {
            if (str.charAt(i++) == '-') sign = -1;
        }
        if (i >= str.length() || !Character.isDigit(str.charAt(i))) return 0;
        long res = 0L;
        while (i < str.length() && Character.isDigit(str.charAt(i))) {
            // if (res > Integer.MAX_VALUE / 10 || res == Integer.MAX_VALUE / 10 && str.charAt(i) - '0' > 7) {
            //     return sign > 0 ? Integer.MAX_VALUE : Integer.MIN_VALUE;
            // }
            
            res = res * 10 + (str.charAt(i) - '0');
            if (res > Integer.MAX_VALUE) {
                return sign > 0 ? Integer.MAX_VALUE : Integer.MIN_VALUE;
            }
            i++;
        }
        return (int)res * sign;
    }
