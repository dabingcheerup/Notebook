![](/assets/Screen Shot 2017-08-23 at 7.42.14 PM.png)
#Analysis
####Idea:
1. 与two sum相似
用left表示左边下标， right表示右边下标，如果numbers[left]+numbers[right]<target，则left++,如果numbers[left]+numbers[right]>target，则right--.如果正好相等，就退出，找到了对应的元素下标

```
public class Solution {
    /*
     * @param nums an array of Integer
     * @param target = nums[index1] + nums[index2]
     * @return [index1 + 1, index2 + 1] (index1 < index2)
     */
    public int[] twoSum(int[] nums, int target) {
        // write your code here
        int left = 0, right = nums.length - 1;
        // 不用判断nums == null
        int[] res = new int[2];
        while (left < right) {
            if (nums[left] + nums[right] == target) {
                res[0] = left + 1;
                res[1] = right + 1;
                break;
            } else if (nums[left] + nums[right] < target) {
                left++;
            } else {
                right--;
            }
        }
        return res;
    }
}
```

