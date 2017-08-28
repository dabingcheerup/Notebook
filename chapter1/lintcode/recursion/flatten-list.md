![](/assets/Screen Shot 2017-08-28 at 5.08.28 PM.png)
#Analysis
####Idea:
recursion
1. 判断是不是integer 是加入result，不是再继续递归地调用函数
non-recursion
1. 


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
public class Solution {

    // @param nestedList a list of NestedInteger
    // @return a list of integer
    public List<Integer> flatten(List<NestedInteger> nestedList) {
        // recursion
        // stores result
        List<Integer> result = new ArrayList<Integer>();
        for (NestedInteger ele: nestedList) {     //?????
            if (ele.isInteger()) {    // 是integer直接加入result中
                result.add(ele.getInteger());  // 不是integer是一个list就调用flatten函数层层分解
            } else {
                result.addAll(flatten(ele.getList()));
            }
        } 
        return result;
    }
}
```


```
//non-recursive version
public class Solution {

    // @param nestedList a list of NestedInteger
    // @return a list of integer
    public List<Integer> flatten(List<NestedInteger> nestedList) {
        boolean isFlat = true;
        List<NestedInteger> ls = nestedList;
        while (isFlat) {
            isFlat = false;
            List<NestedInteger> newLs = new ArrayList<>();
            for (NestedInteger ni : ls) {
                if (ni.isInteger()) {
                    newLs.add(ni);
                } else {
                    newLs.addAll(ni.getList());
                    isFlat = true;
                }
            }
            ls = newLs;
        }
        List<Integer> r = new ArrayList<>();
        for (NestedInteger ni : ls) {
            r.add(ni.getInteger());
        }
        return r;
    }
}
```

####知识点：
1. element.isInteger()
2. element.getInteger()
3. result.addAll()

![](/assets/Screen Shot 2017-08-28 at 5.08.50 PM.png)