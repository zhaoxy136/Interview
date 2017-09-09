### Description
[215M](https://leetcode.com/problems/kth-largest-element-in-an-array/description/)

### Solution

    class Solution {
    public int findKthLargest(int[] nums, int k) {
        return helper(nums, k, 0, nums.length - 1);
    }
    
    public int helper(int[] nums, int k, int start, int end) {
        int index = partition(nums, start, end);
        int count = end - index;
        if (count < k - 1) {
            return helper(nums, k - count - 1, start, index - 1);
        } else if (count > k - 1) {
            return helper(nums, k, index + 1, end);
        } else {
            return nums[index];
        }
    }
    
    public int partition(int[] nums, int start, int end) {
        int pIndex = getPivot(nums, start, end);
        swap(nums, pIndex, end);
        int p = nums[end];
        int i = start - 1;
        int j = start;
        while (j <= end) {
            if (nums[j] <= p) {
                swap(nums, ++i, j);
            }
            j++;
        }
        return i;
    }
    
    public void swap(int[] nums, int i, int j) {
        int tmp = nums[i];
        nums[i] = nums[j];
        nums[j] = tmp;
    }
    
    public int getPivot(int[] nums, int start, int end) {
        int mid = start + (end - start) / 2;
        if (nums[start] > nums[end]) {
            return nums[mid] > nums[end] ? mid : end;
        } else {
            return nums[start] < nums[mid] ? mid : start;
        }
    }
}
