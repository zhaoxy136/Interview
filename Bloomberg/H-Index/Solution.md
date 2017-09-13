### Description
[274M](https://leetcode.com/problems/h-index/description/)

### Solution

    public int hIndex(int[] citations) {
        if (citations == null || citations.length == 0) return 0;
        int n = citations.length;
        
        int[] buckets = new int[n + 1];
        for (int cite : citations) {
            if (cite >= n) {
                buckets[n]++;
            } else {
                buckets[cite]++;
            }
        }
        
        int count = 0;
        for (int i = n; i >= 0; i--) {
            count += buckets[i];
            if (count >= i) return i;
        }
        return 0;
    }
    
### Similar
[H-Index II: 275M](https://leetcode.com/problems/h-index-ii/description/)

    public int hIndex(int[] citations) {
        if (citations == null || citations.length == 0) return 0;
        int n = citations.length;
        int start = 0, end = n - 1;
        while (start <= end) {
            int mid = start + ((end - start) >> 1);
            if (citations[mid] > n - mid) {
                end = mid - 1;
            } else if (citations[mid] < n - mid) {
                start = mid + 1;
            } else {
                return citations[mid];
            }
        }
        return n - start;
    }
