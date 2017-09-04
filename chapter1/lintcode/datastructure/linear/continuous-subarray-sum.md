![](/assets/Screen Shot 2017-09-02 at 11.29.35 AM.png)
#Analysis
####Idea:
与Maximum Subarray类似。
idea: 遍历数组，到i时，记录以i结尾的数组的最大值：
1) 若以i-1元素结尾的最大值小于0，则以i元素结尾的最大值为i元素
2) 若以i-1元素结尾的最大值大于等于0，则以i元素结尾的最大值为以i-1元素结尾的最大值加上i元素



```
public class Solution {
    /**
     * @param A an integer array
     * @return  A list of integers includes the index of the first number and the index of the last number
     */
    public ArrayList<Integer> continuousSubarraySum(int[] A) {
        // Write your code here
        ArrayList<Integer> result = new ArrayList<Integer>();
        // Initialize first index and last index
        result.add(0);
        result.add(0);
        int len = A.length;
        int start = 0, end = 0;
        int sum = 0;
        int ans = -0x7fffffff;
        for (int i = 0; i < len; i++) {
            if (sum < 0) {
                sum = A[i];
                start = end = i;
            } else {
                sum += A[i];
                end = i;
            }
            if (sum > ans) {
                ans = sum;
                result.set(0, start);
                result.set(1, end);
            }
        }
        return result;
    }
}
```

