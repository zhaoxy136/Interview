### Description
[179M](https://leetcode.com/problems/largest-number/description/)

### Solution

    public String largestNumber(int[] nums) {
        String[] strs = new String[nums.length];
        for (int i = 0; i < nums.length; i++) {
            strs[i] = "" + nums[i];
        }
        Arrays.sort(strs, new Comparator<String>(){
            @Override
            public int compare(String s1, String s2) {
                String str1 = s1 + s2;
                String str2 = s2 + s1;
                return str2.compareTo(str1);
            }
        });
        if (strs[0].charAt(0) == '0') return "0";
        String res = "";
        //StringBuilder
        for (String str : strs) {
            res += str;
        }
        return res;
    }
