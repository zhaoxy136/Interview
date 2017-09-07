### Description
[232E](https://leetcode.com/problems/implement-queue-using-stacks/description/)

### Solution

    Stack<Integer> st1;
    Stack<Integer> st2;
    Integer top = null;
    //Integer top;
    /** Initialize your data structure here. */
    public MyQueue() {
        st1 = new Stack<>();
        st2 = new Stack<>();
    }
    
    /** Push element x to the back of queue. */
    public void push(int x) {
        if (st1.isEmpty()) {
            top = x;
        }
        st1.push(x);
    }
    
    /** Removes the element from in front of queue and returns that element. */
    public int pop() {
        if (st2.isEmpty()) {
            while (!st1.isEmpty()) {
                st2.push(st1.pop());
            }
        }
        return st2.pop();
    }
    
    /** Get the front element. */
    public int peek() {
        if (st2.isEmpty()) {
            return top;
        }
        return st2.peek();
    }
    
    /** Returns whether the queue is empty. */
    public boolean empty() {
        return st1.isEmpty() && st2.isEmpty();
    }
    
### Similar
[Implement Stack using Queues: 225E](https://leetcode.com/problems/implement-stack-using-queues/description/)
