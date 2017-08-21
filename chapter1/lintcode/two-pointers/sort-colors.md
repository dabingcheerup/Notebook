![](/assets/Screen Shot 2017-08-21 at 10.49.33 AM.png)
# Analysis
#### Idea:
1. 用三个指针：left：记录第一个为1的位置、right：记录第一个不为2的位置、i：当前需要判断的位置
2. 初始化 left = 0、right = nums.length - 1、 i = 0  
3. while i <= right
4. 若nums[i] = 0，就与第一个1即left交换，left挪到下一个位置，i挪到下一个位置继续判断  若nums[i] = 1，则略过，i继续往下走  若nums[i] = 2, 就与第一个不为2的数交换即right，因为不确定该数nums[right]是0还是1，所以i不变，再判断一次，而right往前挪一位更新标记第一个不为2的数


```
class Solution {
    /**
     * @param nums: A list of integer which is 0, 1 or 2 
     * @return: nothing
     */
    public void sortColors(int[] nums) {
        // write your code here
        if (nums == null || nums.length <= 1) {
            return;
        }
        int left = 0, right =nums.length - 1, i = 0;
        while (i <= right) { // wrong: i < right
            if (nums[i] == 0) {
                swap(nums, i, left);
                left++;
                i++;
            } else if (nums[i] == 1) {
                i++;
            } else { //nums[i] == 2
                swap(nums, right, i); 
                right--;
            }
        }
    }
    private void swap (int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```

#### Wrong Case:
![](/assets/Screen Shot 2017-08-21 at 10.54.56 AM.png)
eg. nums = [1, 0, 1, 2, 2,0]
1. 当i = right = 4 时，是 [0, 0, 1, 1, 0, 2] 还要进行一次i的判断，把0换到第一个为1的位置，所以while的条件应为 i <= right, 否则没法进行
#### 知识点：
1. 交换叫swap

