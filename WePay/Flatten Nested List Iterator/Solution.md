[LeetCode: 341M]()

Solution:

    public class NestedIterator implements Iterator<Integer> {
    Stack<Integer> st;
    public NestedIterator(List<NestedInteger> nestedList) {
        this.st = new Stack<>();
        addToStack(nestedList);
    }

    @Override
    public Integer next() {
        return st.pop();
    }

    @Override
    public boolean hasNext() {
        return !st.isEmpty();
    }
    public void addToStack(List<NestedInteger> list) {
        for (int i = list.size() - 1; i >= 0; i--) {
            NestedInteger tmp = list.get(i);
            if (!tmp.isInteger()) {
                addToStack(tmp.getList());
            } else {
                st.push(tmp.getInteger());
            }
        }
    }
    }
