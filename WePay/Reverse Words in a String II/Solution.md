### Description
[186M](https://leetcode.com/problems/reverse-words-in-a-string-ii/description/)

### Solution

    public void reverseWords(char[] s) {
        //step 1: reverse each word
        //step 2: reverse the whole string
        if (s == null || s.length == 0) return;
        int i = 0;
        while (i < s.length) {
            int j = i + 1;
            while (j < s.length && s[j] != ' ') j++;
            reverse(s, i, j-1);
            i = j + 1;
        }
        reverse(s, 0, s.length - 1);
    }
    
    public void reverse(char[] s, int start, int end) {
        while (start < end) {
            char c = s[start];
            s[start++] = s[end];
            s[end--] = c;
        }
    }

### Similar
[151M](https://leetcode.com/problems/reverse-words-in-a-string/description/)


