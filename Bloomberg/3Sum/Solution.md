### Description
[15M](https://leetcode.com/problems/3sum/description/)

### Solution

    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        if (nums.length < 3) return res;
        Arrays.sort(nums);
        for (int i = 0; i < nums.length - 2; i++) {
            if (i > 0 && nums[i] == nums[i-1]) continue;
            int start = i + 1, end = nums.length - 1;
            while (start < end) {
                if (nums[i] + nums[start] < -nums[end]) {
                    start++;
                } else if (nums[i] + nums[start] > -nums[end]) {
                    end--;
                } else {
                    List<Integer> list = new ArrayList<>();
                    list.add(nums[i]);
                    list.add(nums[start]);
                    list.add(nums[end]);
                    res.add(list);
                    while (++start < end && nums[start] == nums[start-1]);
                    while (start < --end && nums[end] == nums[end+1]);
                }
            }
        }
        return res;
    }

### Similar
[3 Sum Closest](https://leetcode.com/problems/3sum-closest/description/)

    public int threeSumClosest(int[] nums, int target) {
        if (nums.length < 3) return 0;
        Arrays.sort(nums);
        long res = Integer.MAX_VALUE;
        for (int i = 0; i < nums.length - 2; i++) {
            if (i > 0 && nums[i] == nums[i-1]) continue;
            int start = i + 1;
            int end = nums.length - 1;
            while (start < end) {
                long val = nums[i] + nums[start] + nums[end];
                if (Math.abs(val - target) < Math.abs((long)res - target)) {
                    res = val;
                }
                if (val < target) {
                    while (nums[start] == nums[++start] && start < end);
                } else if (val > target) {
                    while (nums[end] == nums[--end] && start < end);
                } else {
                    return target;
                }
            }
        }
        return (int)res;
    }
