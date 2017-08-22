![](/assets/Screen Shot 2017-08-22 at 10.19.56 AM.png)
#Analysis
####Idea:
与前一道题基本相同
1. 额外用一个boolean表示是否可以添加重复元素，只有boolean为true时才能添加重复元素。当添加一个新元素时，boolean设置为true，当添加一个重复元素后，boolean设置为false。


```
public class Solution {
    /**
     * @param A: a array of integers
     * @return : return an integer
     */
    public int removeDuplicates(int[] nums) {
        // write your code 
        if (nums == null || nums.length == 0) {
            return 0;
        }
        boolean twice = true;
        int i = 0;
        for (int j = 1; j < nums.length; j++) {
            if (nums[i] != nums[j]) {
                i++;
                nums[i] = nums[j];
                twice = true; 
            } else if (twice) {
                i++;
                nums[i] = nums[j];
                twice = false;
            }
        }
        return i + 1;
    }
}
```

