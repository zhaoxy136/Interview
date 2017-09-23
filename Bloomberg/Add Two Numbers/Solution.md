### Description
[445M](https://leetcode.com/problems/add-two-numbers-ii/description/)   

### Solution

    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        Stack<Integer> st1 = new Stack<>();
        Stack<Integer> st2 = new Stack<>();
        while (l1 != null) {
            st1.push(l1.val);
            l1 = l1.next;
        }
        while (l2 != null) {
            st2.push(l2.val);
            l2 = l2.next;
        }
        ListNode head = null;
        ListNode cur = null;
        int carry = 0;
        while (!st1.isEmpty() || !st2.isEmpty() || carry != 0) {
            if (!st1.isEmpty()) {
                carry += st1.pop();
            }
            if (!st2.isEmpty()) {
                carry += st2.pop();
            }
            cur = new ListNode(carry % 10);
            carry /= 10;
            cur.next = head;
            head = cur;
        }
        return head;
    }

while poping from the stack, construct the list from end to begin

### Similar
[Add Binary :67E](https://leetcode.com/problems/add-binary/description/)  
[Add Two String: 415E](https://leetcode.com/problems/add-strings/description/)
[Add Two Numbers: 2M](https://leetcode.com/problems/add-two-numbers/description/)  
[Sum of Two Integers: 317E](https://leetcode.com/problems/sum-of-two-integers/description/)
[Multiply Strings: 43M](https://leetcode.com/problems/multiply-strings/description/)
