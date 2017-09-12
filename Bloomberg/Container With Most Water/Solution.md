### Description
[11M](https://leetcode.com/problems/container-with-most-water/description/)

### Solution

    public int maxArea(int[] height) {
        int res = 0;
        int i = 0, j = height.length - 1;
        while (i < j) {
            int h = Math.min(height[i], height[j]);
            int w = j - i;
            res = Math.max(res, h * w);
            if (height[i] < height[j]) {
                i++;
            } else {
                j--;
            }
        }
        return res;
    }
