### Descriptioin
[53E](https://leetcode.com/problems/maximum-subarray/description/)

### Solution

    public int maxSubArray(int[] nums) {
        if (nums == null || nums.length == 0) return 0;
        int res = nums[0];
        int max = nums[0];
        for (int i = 1; i < nums.length; i++) {
            max = Math.max(max + nums[i], nums[i]);
            res = Math.max(res, max);
        }
        return res;
    }

### Similar
[Maximum Product Subarray: 152M](https://leetcode.com/problems/maximum-product-subarray/description/)
