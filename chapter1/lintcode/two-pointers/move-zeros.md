![](/assets/Screen Shot 2017-08-23 at 2.42.17 PM.png)
#Analysis
####Idea:
与remove element相似
1. two pointer 初始化 left = 0 第一个为0的数 right 第一个不为0的数
2. 交换 直到right到底


```
public class Solution {
    /**
     * @param nums an integer array
     * @return nothing, do this in-place
     */
    public void moveZeroes(int[] nums) {
        // Write your code here
        int left = 0, right = 0;
        while (right < nums.length) {
            if (nums[right] != 0) {
                int temp = nums[left];
                nums[left] = nums[right];
                nums[right] = temp;
                left++;
            }
            right++;
        }
    }
}
```

