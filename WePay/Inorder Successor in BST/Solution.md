### Description
[285M](https://leetcode.com/problems/inorder-successor-in-bst/description/)

### Solution

    public TreeNode inorderSuccessor(TreeNode root, TreeNode p) {
        if (p == null) return null;
        TreeNode cur = root;
        TreeNode prev = null;
        while (cur != null) {
            if (p.val < cur.val) {
                prev = cur;
                cur = cur.left;
            } else {
                cur = cur.right;
            }
        }
        return prev;
    }
