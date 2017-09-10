### Description
[141E](https://leetcode.com/problems/linked-list-cycle/description/)

### Solution

    public boolean hasCycle(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow == fast) return true;
        }
        return false;
    }
    
### Similar
[Linked List Cycle II : 142M](https://leetcode.com/problems/linked-list-cycle-ii/description/)

    public ListNode detectCycle(ListNode head) {
        if (head == null || head.next == null) return null;
        ListNode slow = head;
        ListNode fast = head.next;
        while (slow != fast) {
            if (fast == null || fast.next == null) return null;
            slow = slow.next;
            fast = fast.next.next;
        }
        slow = head;
        fast = fast.next;    
        while (slow != fast) {
            slow = slow.next;
            fast = fast.next;
        }
        return slow;
    }
