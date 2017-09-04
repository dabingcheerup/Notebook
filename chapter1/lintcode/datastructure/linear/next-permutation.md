![](/assets/Screen Shot 2017-09-03 at 10.34.11 AM.png)
#Analysis
####Idea:
思想基本和I一样。
首先找到需要变大的那一位。因为求的是next permutation，所以增大位数要尽量靠右边同时增大的数值要尽量小。具体方法如下：
1)  从数组尾部开始，依次找最后一个比之前的数大的数，即升序的最后一个，index记录该数的前一个数的index。如果index还是初始化的-1，证明整个数组是降序，直接reverse。
2） 再从后往前找第一个比nums[index]要大的数，其index标记为biggerIndex.然后交换两者
3） 再把index+1 ~ nums.length-1 之间的数reverse



```
public class Solution {
    /**
     * @param nums: an array of integers
     * @return: return nothing (void), do not return anything, modify nums in-place instead
     */
    public void reverse(int[] nums, int start, int end) {
        for (int i = start, j = end; i < j; i++, j--) {
            int temp = nums[i];
            nums[i] = nums[j];
            nums[j] = temp;
        }
    }
    public void nextPermutation(int[] nums) {
        // write your code here
        // find the last increase index
        int index = -1;
        // 从后往前找快
        for (int i = nums.length - 2; i >= 0; i--) {
            if (nums[i] < nums[i + 1]) {
                index = i;
                break;
            }
        }
        // 如果从后往前遍历都没有找到，证明num是个降序数组，直接reverse后返回结果即可
        if (index == -1) {
            reverse(nums, 0, nums.length - 1);
            return;
        }
        // find  the first bigger than nums[index]
        int biggerIndex = index + 1;
        for (int i = nums.length -1; i > index; i--) {
            if (nums[i] > nums[index]) {
                biggerIndex = i;
                break;
            }
        }
        // swap them to make the permutation bigger
        int temp = nums[index];
        nums[index] = nums[biggerIndex];
        nums[biggerIndex] = temp;
        // reverse the last part
        reverse(nums, index + 1, nums.length - 1);
    }
}
```
![](/assets/Screen Shot 2017-09-03 at 11.33.06 AM.png)
