![](/assets/Screen Shot 2017-08-21 at 5.44.12 PM.png)

# Analysis

#### Idea:

与sort colors相似  
1. left从0开始扫  
    1.扫到value就把当前right指向的放到left中等过后判断是否为vale，然后right--就相当于找到一个value  
    2.left没扫到value，就继续找，left++  
3. 返回right + 1以前的

**left从0开始找value就把right放到left上（等下还要在判断），然后right--相当于把value挪到后面了**

#### Error:

1.退出条件： left &lt;= right  
    input: \[3,3\] 3  
    expected output: \[\]

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



