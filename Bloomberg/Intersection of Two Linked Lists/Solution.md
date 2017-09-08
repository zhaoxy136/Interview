### Description
[160E](https://leetcode.com/problems/intersection-of-two-linked-lists/description/)

### Solution

    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        ListNode l1 = headA;
        ListNode l2 = headB;
        while (l1 != null && l2 != null) {
            if (l1 == l2) return l1;
            l1 = l1.next;
            l2 = l2.next;
            if (l1 == null) {
                l1 = headB;
            } else if (l2 == null) {
                l2 = headA;
            }
        }
        return null;
    }
