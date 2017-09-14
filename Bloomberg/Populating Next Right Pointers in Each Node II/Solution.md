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

Version 1: Queue

    public void connect(TreeLinkNode root) {
        if (root == null) return;
        Queue<TreeLinkNode> queue = new LinkedList<>();
        queue.add(root);
        while (!queue.isEmpty()) {
            TreeLinkNode next = null;
            int size = queue.size();
            while (size-- > 0) {
                TreeLinkNode tmp = queue.poll();
                tmp.next = next;
                if (tmp.right != null) queue.add(tmp.right);
                if (tmp.left != null) queue.add(tmp.left);
                next = tmp;
            }        
        }
    }
