### Description
[24M](https://leetcode.com/problems/swap-nodes-in-pairs/description/)

### Solution

    public ListNode swapPairs(ListNode head) {
        if (head == null || head.next == null) return head;
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode prev = dummy;
        ListNode cur = head;
        while (prev.next != null && prev.next.next != null) {
            ListNode tmp = prev.next;
            prev.next = tmp.next;
            tmp.next = prev.next.next;
            prev.next.next = tmp;
            prev = tmp;
        }
        return dummy.next;
    }
    
### Similar
[Reverse Nodes in k-Group: 25H](https://leetcode.com/problems/reverse-nodes-in-k-group/description/)
Recursive

    public ListNode reverseKGroup(ListNode head, int k) {
        ListNode cur = head;
        for (int i = 0; i < k; i++) {
            if (cur == null) return head;
            cur = cur.next;
        }
        cur = reverseKGroup(cur, k);
        while (k-- > 0) {
            ListNode tmp = head.next;
            head.next = cur;
            cur = head;
            head = tmp;
        }
        return cur;
    }

Iterative

    public ListNode reverseKGroup(ListNode head, int k) {
        if (head == null || k <= 1) return head;
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode prev = dummy;
        ListNode cur = head;
        while (needReverse(cur, k)) {
            int n = k;
            while (--n > 0) {
                ListNode tmp = cur.next;
                cur.next = tmp.next;
                tmp.next = prev.next;
                prev.next = tmp;
            }
            prev = cur;
            cur = cur.next;
        }
        return dummy.next;
    }
    
    public boolean needReverse(ListNode head, int k) {
        for (int i = 0; i < k; i++) {
            if (head == null) return false;
            head = head.next;
        }
        return true;
    }
