### Description
[42H](https://leetcode.com/problems/trapping-rain-water/description/)
### Solution

    public int trap(int[] height) {
        if (height.length < 3) return 0;
        int leftBound = height[0];
        int rightBound = height[height.length - 1];
        int left = 1;
        int right = height.length - 2;
        int res = 0;
        while (left <= right) {
            if (leftBound < rightBound) {
                if (height[left] < leftBound) {
                    res += leftBound - height[left];
                } else {
                    leftBound = height[left];
                }
                left++;
            } else {
                if (height[right] < rightBound) {
                    res += rightBound - height[right];
                } else {
                    rightBound = height[right];
                }
                right--;
            }
        }
        return res;
    }
    
### Similar
[LeetCode: 407H](https://leetcode.com/problems/trapping-rain-water-ii/description/)
