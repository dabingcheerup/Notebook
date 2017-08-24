![](/assets/Screen Shot 2017-08-22 at 10.08.16 PM.png)
#Analysis
####Idea:
two pointer
1. 遍历数组，到i时，找到以i元素开头的最短的子数组，若比最短子数组小则更新。

```
public class Solution {
    /**
     * @param nums: an array of integers
     * @param s: an integer
     * @return: an integer representing the minimum size of subarray
     */
    public int minimumSize(int[] nums, int s) {
        // write your code here
        if (nums == null || nums.length == 0) {
            return -1;
        }
        int min = Integer.MAX_VALUE;
        for (int i = 0; i < nums.length; i++) {
            int count = i;
            int sum = nums[count];
            while (sum < s) {
                count++;
                if (count >= nums.length) {
                    break;
                }
                sum += nums[count];
            }
            if (count >= nums.length) {
                break;
            }
            min = Math.min(min, count - i + 1);
        }
        if (min == Integer.MAX_VALUE) {
            return -1;
        }
        return min;
    }
}
```

