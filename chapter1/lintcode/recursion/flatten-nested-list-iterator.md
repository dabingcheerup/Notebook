![](/assets/Screen Shot 2017-08-29 at 10.21.55 AM.png)
#Analysis
与Flatten List类似，但是那道题用递归的方式，而这道题要求用迭代的方式。
迭代可以利用stack来完成。先将list中所有元素从后往前压入栈中。在hasNext()中，首先判断栈是否为空，若不为空再判断栈顶元素是整数还是list，若是整数则返回true，若是list则移除栈顶元素，并将其中元素按从后往前压入栈中，并再次从头执行hasNext的步骤，直到栈为空则返回false。next则直接取出栈顶元素并返回其值（根据hasNext，一定为整数而非list）。



```
/**
 * // This is the interface that allows for creating nested lists.
 * // You should not implement it, or speculate about its implementation
 * public interface NestedInteger {
 *
 *     // @return true if this NestedInteger holds a single integer,
 *     // rather than a nested list.
 *     public boolean isInteger();
 *
 *     // @return the single integer that this NestedInteger holds,
 *     // if it holds a single integer
 *     // Return null if this NestedInteger holds a nested list
 *     public Integer getInteger();
 *
 *     // @return the nested list that this NestedInteger holds,
 *     // if it holds a nested list
 *     // Return null if this NestedInteger holds a single integer
 *     public List<NestedInteger> getList();
 * }
 */
import java.util.Iterator;

public class NestedIterator implements Iterator<Integer> {

    private Stack<NestedInteger> stack; // private 在这的作用
    private void pushListToStack(List<NestedInteger> nestedList) {
        Stack<NestedInteger> temp = new Stack<>();
        for (NestedInteger nested : nestedList) { //遍历nestedList??
            temp.push(nested); // stack 先进后出 push的元素头在底部
        }
        while (!temp.isEmpty()) { // 再来个stack 把元素头放到顶部
            stack.push(temp.pop());
        }
    }
    public NestedIterator(List<NestedInteger> nestedList) {
        // Initialize your data structure here.
        stack = new Stack<>(); //??? 初始化？
        pushListToStack(nestedList); // 调用上面的函数；
    }

    // @return {int} the next element in the iteration
    @Override
    public Integer next() {
        // Write your code here
        if (!hasNext()) {
            return null;
        }
        return stack.pop().getInteger();
    }

    // @return {boolean} true if the iteration has more element or false
    @Override
    public boolean hasNext() {
        // Write your code here
        while (!stack.isEmpty() && !stack.peek().isInteger()) {
            pushListToStack(stack.pop().getList());
        }
        return !stack.isEmpty();
    }

    @Override
    public void remove() {}
}

/**
 * Your NestedIterator object will be instantiated and called as such:
 * NestedIterator i = new NestedIterator(nestedList);
 * while (i.hasNext()) v.add(i.next());
 */
```
####知识点：
1. Stack<NestedInteger> temp = new Stack<>(); stack = new Stack<>(); temp.push(nested); temp.isEmpty();  stack.pop().getInteger(); stack.peek().isInteger(); stack.pop().getList()
2. for (NestedInteger nested : nestedList)
3. hasNext();