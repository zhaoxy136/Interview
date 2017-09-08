### Description

[98M](https://leetcode.com/problems/validate-binary-search-tree/description/)

### Solution
Version 0: using Auxiliary Class

Version 1: clever recursion

    class Solution {
    public boolean isValidBST(TreeNode root) {
        return helper(root, Long.MIN_VALUE, Long.MAX_VALUE);
    }
    
    public boolean helper(TreeNode root, long minVal, long maxVal) {
        if (root == null) return true;
        if (minVal >= root.val || maxVal <= root.val) return false;
        return helper(root.left, minVal, root.val) && helper(root.right, root.val, maxVal);
    }
    }
