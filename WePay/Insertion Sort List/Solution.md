[LeetCode:147M](https://leetcode.com/problems/insertion-sort-list/description/)

Solution:

    class Solution {
    public ListNode insertionSortList(ListNode head) {
        if (head == null || head.next == null) return head;
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode prev = head;
        ListNode cur = head.next;
        while (cur != null) {
            if (cur.val >= prev.val) {
                prev = cur;
                cur = cur.next;
            } else {
                prev.next = cur.next;
                ListNode tmp = dummy;
                while (tmp.next.val < cur.val) {
                    tmp = tmp.next;
                }
                cur.next = tmp.next;
                tmp.next = cur;
                cur = prev.next;
            }
        }
        return dummy.next;
    }
    }
