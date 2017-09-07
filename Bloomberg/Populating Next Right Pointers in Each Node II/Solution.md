### Description
[117M](https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/description/)

### Solution

    public void connect(TreeLinkNode root) {
        TreeLinkNode head = new TreeLinkNode(0);
        TreeLinkNode prev = head;
        while (root != null) {
            if (root.left != null) {
                prev.next = root.left;
                prev = prev.next;
            }
            if (root.right != null) {
                prev.next = root.right;
                prev = prev.next;
            }
            root = root.next;
            if (root == null) {
                root = head.next;
                head.next = null;
                prev = head;
            }
        }
    }
