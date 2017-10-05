Description: implement double sqrt(double x);

Solution:
//需要设定精度，不然会死循环
//Newton Method:

    public static double sqrt(double x) {
        if (x == 0) return 0;
        double res = x;
        while (res * res > x) {
            if (Math.abs(x/res - res) < 0.00001) break;
            res = (res + x / res) / 2;
        }
        return res;
    }
    
//BS
//慢于第一种方法
    
    public static double sqrt(double x) {
        if (x == 0) return 0;
        double start = 0;
        double end = x;
        while (start + 0.0001 < end) {
            double mid = start + (end - start) / 2;
            if (mid > x / mid) {
                end = mid - 0.001;
            } else {
                start = mid;
            }
        }
        return start;
    }
