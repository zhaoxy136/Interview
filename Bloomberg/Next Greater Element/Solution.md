### Description
[496E](https://leetcode.com/problems/next-greater-element-i/)  
[503M](https://leetcode.com/problems/next-greater-element-ii/description/)  
[556M](https://leetcode.com/problems/next-greater-element-iii/description/)  

### Solution

Next Greater Element I

    public int[] nextGreaterElement(int[] nums1, int[] nums2) {
        Stack<Integer> st = new Stack<>();
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums2.length; i++) {
            while (!st.isEmpty() && nums2[i] > st.peek()) {
                map.put(st.pop(), nums2[i]);
            }
            st.push(nums2[i]);
        }
        
        int[] res = new int[nums1.length];
        for (int i = 0; i < nums1.length; i++) {
            res[i] = map.getOrDefault(nums1[i], -1);
        }
        return res;
    }

Next Greater Element II

    public int[] nextGreaterElements(int[] nums) {
        int[] res = new int[nums.length];
        Stack<Integer> st = new Stack<>();
        for (int i = nums.length - 1; i >= 0; i--) {
            st.push(nums[i]);
        }
        for (int i = nums.length - 1; i >= 0; i--) {
            while (!st.isEmpty() && st.peek() <= nums[i]) {
                st.pop();
            }
            res[i] = st.isEmpty() ? -1 : st.peek();
            st.push(nums[i]);
        }
        return res;
    }
    
    
Next Greater Element III

    public int nextGreaterElement(int n) {
        char[] nums = String.valueOf(n).toCharArray();
        int i = nums.length - 1;
        while (i > 0 && nums[i] <= nums[i-1]) i--;
        if (i == 0) return -1;
        int j = nums.length - 1;
        while (j >= i && nums[j] <= nums[i-1]) j--;
        
        char c = nums[i-1];
        nums[i-1] = nums[j];
        nums[j] = c;
        
        j = nums.length - 1;
        while (i < j) {
            c = nums[i];
            nums[i++] = nums[j];
            nums[j--] = c;
        }
        long res = Long.parseLong(new String(nums));
        return res > Integer.MAX_VALUE ? -1 : (int)res;
    }
    
    
