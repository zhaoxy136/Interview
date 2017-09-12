### Description
[230M](https://leetcode.com/problems/kth-smallest-element-in-a-bst/description/)

### Solution

    public int kthSmallest(TreeNode root, int k) {
        int count = 0;
        Stack<TreeNode> st = new Stack<>();
        TreeNode p = root;
        while (p != null || !st.isEmpty()) {
            while (p != null) {
                st.push(p);
                p = p.left;
            }
            p = st.pop();
            if (++count == k) return p.val;
            p = p.right;
        }
        return -1;
    }
    



### Follow UP
What if the BST is modified (insert/delete operations) often and you need to find the kth smallest frequently? 
How would you optimize the kthSmallest routine?

    public class Solution {
        public int kthSmallest(TreeNode root, int k) {
            int left = nodeCount(root.left);  // this value can be saved in the root node
            if(left + 1 == k) {
                return root.val;
            } else if (left + 1 < k) {
                return kthSmallest(root.right, k - left - 1);
            } else {
                return kthSmallest(root.left, k);
            }
        }
        
        private int nodeCount(TreeNode root) {
            if(root == null) {
                return 0;
            }
            return 1 + nodeCount(root.left) + nodeCount(root.right);
        }
    }
