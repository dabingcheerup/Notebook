![](/assets/Screen Shot 2017-08-21 at 5.44.12 PM.png)
# Analysis
#### Idea:
与sort colors相似
1. two pointers left: 当前字符 right: 可被替换的
2. 前后扫，前面扫到elem, 与right替换，换到前面后left不变，再判断一次。因为换到前面的可能也是elem, 这样一直前后找elem,直到left和right相遇。
3. 返回right + 1以前的

####Error:
1.退出条件： left <= right
    input: [3,3] 3
    expected output: []



```
public class Solution {
    /** 
     *@param A: A list of integers
     *@param elem: An integer
     *@return: The new length after remove
     */
    public int removeElement(int[] A, int elem) {
        // write your code here
        int left = 0;
        int right = A.length - 1;
        while (left <= right) {
            if (A[left] == elem) {
                A[left] = A[right];
                right--;
            } else{
                left++;
            }
        }
        return right + 1;
    }
}

```

