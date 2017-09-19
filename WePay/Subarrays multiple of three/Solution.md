### Description
Given an array, get the number of subarrays whose sum are multiples of 3.

### Solution
//Version 0: O(n2), preSum

    public static int multOfThree(int[] nums) {
        long[] preSum = new long[nums.length + 1];

        for (int i = 0; i < nums.length; i++) {
            preSum[i+1] = preSum[i] + nums[i];
        }
        int res = 0;
        for (int i = 1; i <= nums.length; i++) {
            for (int j = 0; j < i; j++) {
                if ((preSum[i] - preSum[j]) % 3 == 0) {
                    res++;
                }
            }
        }
        return res;
    }
    
//Version 1: O(n), expand to K

    public static int multOfK(int[] nums, int k) {
        if (nums == null || nums.length == 0) return 0;
        int[] count = new int[k];
        long sum = 0L;
        int res = 0;
        for (int num : nums) {
            sum += num;
            int rem = (int)(sum % k);
            if (rem == 0) {
                res += count[rem] + 1;
            } else {
                res += count[rem];
            }
            count[rem]++;
        }
        return res;
    }
    
