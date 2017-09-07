### Description
[158H](https://leetcode.com/problems/read-n-characters-given-read4-ii-call-multiple-times/description/)

### Solution

    public class Solution extends Reader4 {
    /**
     * @param buf Destination buffer
     * @param n   Maximum number of characters to read
     * @return    The number of characters read
     */
    int bufCount = 0;
    int bufIndex = 0;
    char[] buffer = new char[4];
    public int read(char[] buf, int n) {
        int count = 0;
        while (count < n) {
            if (bufIndex == 0) {
                bufCount = read4(buffer);
            }
            if (bufCount == 0) return count;
            while (count < n && bufIndex < bufCount) {
                buf[count++] = buffer[bufIndex++];
            }
            if (bufIndex == bufCount) {
                bufIndex = 0;
            }
        }
        return count;
    }
    }

### Similar
[157E](https://leetcode.com/problems/read-n-characters-given-read4/description/)
