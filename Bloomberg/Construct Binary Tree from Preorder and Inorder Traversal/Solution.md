### Description
[105M](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/)

### Solution

    class Solution {
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        return helper(preorder, 0, inorder, 0, inorder.length - 1);
    }
    
    public TreeNode helper(int[] preorder, int root, int[] inorder, int start, int end) {
        if (start > end) return null;
        TreeNode node = new TreeNode(preorder[root]);
        if (start == end) return node;
        int index = end;
        while (index >= start && inorder[index] != preorder[root]) {
            index--;
        }
        node.left = helper(preorder, root + 1, inorder, start, index - 1);
        node.right = helper(preorder, root + index - start + 1, inorder, index + 1, end);
        return node;
    }
    }
