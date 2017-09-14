### Description
[155E](https://leetcode.com/problems/min-stack/description/)

### Solution
Version 1: two stack

    public Stack<Integer> stack;
    public Stack<Integer> curMin;
    /** initialize your data structure here. */
    public MinStack() {
        stack = new Stack<>();
        curMin = new Stack<>();
    }
    
    public void push(int x) {
        stack.push(x);
        if (curMin.isEmpty() || x <= curMin.peek()) {
            curMin.push(x);
        }
    }
    
    public void pop() {
        int temp = stack.pop();
        if (curMin.peek() == temp) {
            curMin.pop();
        }
    }
    
    public int top() {
        return stack.peek();
    }
    
    public int getMin() {
        return curMin.peek();
    }

Version 2: one stack

    Stack<Long> st;
    long min;
    /** initialize your data structure here. */
    public MinStack() {
        st = new Stack<>();
        min = 0L;
    }
    
    public void push(int x) {
        if (st.isEmpty()) {
            st.push(0L);
            min = x;
        } else {
            long dif = x - min;
            if (dif < 0) {
                min = x;
            }
            st.push(dif);
        }
    }
    
    public void pop() {
        long val = st.pop();
        if (val < 0) {
            min -= val;
        }
    }
    
    public int top() {
        return st.peek() < 0 ? (int)min : (int)(st.peek() + min);
    }
    
    public int getMin() {
        return (int)min;
    }
