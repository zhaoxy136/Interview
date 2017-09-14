### Description
[287M](https://leetcode.com/problems/find-the-duplicate-number/description/)

### Solution

    class Solution {
    public int findDuplicate(int[] nums) {
        if (nums == null || nums.length == 0) return -1;
        int start = 1, end = nums.length - 1;
        while (start < end) {
            int mid = start + (end - start) / 2;
            int count = getCounts(nums, mid);
            if (count >= nums.length - mid) {
                start = mid + 1;
            } else {
                end = mid;
            }
        }
        return start;
    }
    //get the number of elements in the array that is greater than target
    public int getCounts(int[] nums, int target) {
        int count = 0;
        for (int n : nums) {
            if (n > target) count++;
        }
        return count;
    }
    }
    
Version 2:

    class Solution {
    public int findDuplicate(int[] nums) {
        if (nums == null || nums.length == 0) return -1;
        int start = 1, end = nums.length - 1;
        while (start < end) {
            int mid = start + (end - start) / 2;
            int count = getCounts(nums, mid);
            if (count > mid) {
                end = mid;
            } else {
                start = mid + 1;
            }
        }
        return start;
    }
    //get the number of elements in the array that is less than or equal to target
    public int getCounts(int[] nums, int target) {
        int count = 0;
        for (int n : nums) {
            if (n <= target) count++;
        }
        return count;
    }
    }

### Similar
[Missing Number: 268E](https://leetcode.com/problems/missing-number/description/)
