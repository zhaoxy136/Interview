### Problem Description:
[138M](https://leetcode.com/problems/copy-list-with-random-pointer/description/)

### Solution
Version 0: HashMap

    public RandomListNode copyRandomList(RandomListNode head) {
        Map<RandomListNode,RandomListNode> map = new HashMap<>();
        RandomListNode node = head;
        //clone nodes
        while (node != null) {
            map.put(node, new RandomListNode(node.label));
            node = node.next;
        }
        //clone pointers
        for (RandomListNode tmp : map.keySet()) {
            map.get(tmp).next = map.get(tmp.next);
            map.get(tmp).random = map.get(tmp.random);
        }
        return map.get(head);
    }
    
Version 1: O(1) space

    public RandomListNode copyRandomList(RandomListNode head) {
        if (head == null) return null;
        //copy the nodes
        RandomListNode cur = head;
        while (cur != null) {
            RandomListNode node = new RandomListNode(cur.label);
            node.next = cur.next;
            cur.next = node;
            cur = node.next;
        }
        //copy random pointers
        cur = head;
        while (cur != null) {
            //check if random points to null
            cur.next.random = cur.random == null ? null : cur.random.next;
            cur = cur.next.next;
        }
        //copy next pointers and recover original list
        cur = head;
        RandomListNode newHead = head.next;
        while (cur != null) {
            RandomListNode tmp = cur.next;
            cur.next = tmp.next;
            cur = cur.next;
            tmp.next = cur == null ? null : cur.next;
        }
        return newHead;
    }

### Edge case
{-1, #} just one node, both next and random pointer points to null.

