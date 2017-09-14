### Description
[LintCode](http://www.lintcode.com/en/problem/fibonacci/#)

### Solution
Iterative

    public int fibonacci(int n) {
        if (n < 1) return -1;
        if (n < 3) return n - 1;
        int prev = 0;
        int res = 1;
        for (int i = 3; i <= n; i++) {
            int tmp = res;
            res += prev;
            prev = tmp;
        }
        return res;
    }
    
Recursive

    public int fibonacci(int n) {
        if (n < 1) return -1;
        if (n < 3) return n - 1;
        return fibonacci(n - 1) + fibonacci(n - 2);
    }
      
DP
    
    public int fibonacci(int n) {
        if (n < 1) return -1;
        if (n < 3) return n - 1;
        List<Integer> nums = new ArrayList<>();
        nums.add(0);
        nums.add(1);
        for (int i = 2; i < n; i++) {
            int val = nums.get(i - 1) + nums.get(i - 2);
            nums.add(val);
        }
        return nums.get(n-1);
    }
