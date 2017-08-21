![](/assets/Screen Shot 2017-08-20 at 3.06.45 PM.png)
# Anlysis
#### Idea:
此题是in-place的模板，用到三个while
1. two pointers 头尾指针交换
2. 用两个while判断两种情况，判断条件 left <= right && nums[left]< k, 继续挪到左指针； left <= right && nums[right] >= k 继续挪动
3. 若两者情况都不满足，left和right指针停住 可以进行交换


```
public class Solution {
    /*
     * @param nums: The integer array you should partition
     * @param k: An integer
     * @return: The index after partition
     */
    public int partitionArray(int[] nums, int k) {
        // write your code here
        int len = nums.length;
        if (nums == null || len < 1) {
            return 0;
        }
        // Initialize two pointers
        int left = 0, right = len - 1;
        // 头尾相夹逼，直到相遇
        while (left <= right) {
            // make sure left pointer is on the left side of right pointer
            // if nums[left] >= k, left stops moving, wait for exchange
            while (left <= right && nums[left] < k) {
                left++;
            }
            // if nums[right] < k, right stops moving, wait for exchange
            while (left <= right && nums[right] >= k) {
                right--;
            }
            // exchange two value, use three variable
            if (left <= right) {
                int temp = nums[left];
                nums[left] = nums[right];
                nums[right] = temp;
                // complete exchange, then move two pointers
                left++;
                right--;
            }
        }
        return left;
    }
};
```
#### 知识点：
1. 巧用while

