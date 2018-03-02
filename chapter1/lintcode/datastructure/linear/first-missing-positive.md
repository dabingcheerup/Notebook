![](/assets/Screen Shot 2017-09-02 at 11.49.02 AM.png)

```
public class Solution {
    /*
     * @param A: An array of integers
     * @return: An integer
     */
    public int firstMissingPositive(int[] A) {
        // write your code here
        if (A == null) {
            return 1;
        }
        // 遍历第一遍，通过交换把相应的数放到相应的位置, 跳过negative
        for (int i = 0; i < A.length; i++) {
            while (A[i] > 0 && A[i] <= A.length && A[i] != (i + 1)) {
                int temp = A[A[i] - 1];
                if (temp == A[i]) {
                    break;
                }
                A[A[i] - 1] = A[i];
                A[i] = temp;
            }
        }
        // 再遍历一遍，找出不在相应位置的数
        for (int i = 0; i < A.length; i++) {
            if (A[i] != i + 1) {
                return i + 1;
            }
        }
        return A.length + 1;
    }
}
```

#### Reference

[参考1](https://zhengyang2015.gitbooks.io/lintcode/first_missing_positive_189.html)  
![](/assets/Screen Shot 2017-09-02 at 3.33.38 PM.png)

