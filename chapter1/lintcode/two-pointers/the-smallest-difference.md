![](/assets/Screen Shot 2017-08-23 at 11.54.24 AM.png)
#Analysis
####Idea:
1. sort A, B two pointer Ap, Bp 
2. 计算A[Ap] - B[Bp]绝对值 与min比较取最小
3. 根据比较大小，决定如何挪动指针从而找到最小差值


```
public class Solution {
    /**
     * @param A, B: Two integer arrays.
     * @return: Their smallest difference.
     */
    public int smallestDifference(int[] A, int[] B) {
        // write your code here
        if (A == null || A.length == 0 || B == null || B.length == 0) {
            return 0;
        }
        int min = Integer.MAX_VALUE;
        int Ap = 0, Bp = 0;
        // sort A, B
        Arrays.sort(A);
        Arrays.sort(B);
        while (Ap < A.length && Bp < B.length) {
            // 记录最小差值
            min = Math.min(min, Math.abs(A[Ap]-B[Bp]));
            // 根据比较大小，决定如何挪动指针从而找到最小差值
            if (A[Ap] < B[Bp]) {
                Ap++;
            } else {
                Bp++;
            }
        }
        return min;
    }
}

```
![](/assets/Screen Shot 2017-08-23 at 11.57.41 AM.png)

