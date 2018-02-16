![](/assets/Screen Shot 2017-08-22 at 10.08.41 AM.png)

# Analysis

#### Idea:

这是sorted array  
1. two pointer i:标记最后一个不重复的数 j:标记当前扫到的数  
2. 若扫到的数nums\[j\]与nums\[i\]不等，i++指向下一个数，为重复的数，所以nums\[j\]赋值给nums\[i\] 一直下去 result是i + 1  
3. 若扫到的数nums\[j\]与nums\[i\]相等，j++，即i和j之间的数都是重复的
**重点是找到最后一个非重复的位置即i，把找到的unique的数放到它后面即i+1**
#####Error:
1. for(int i = 0, j=1; j < nums.length; j++)
    log:Line 12: error: cannot find symbol: variable i
    改：int i = 0;

```
public class Solution {
    /**
     * @param A: a array of integers
     * @return : return an integer
     */
    public int removeDuplicates(int[] nums) {
        // write your code here
        if (nums == null || nums.length == 0) {
            return 0;
        }
        int i = 0;
        for (int j = 1; j < nums.length; j++) {
            if (nums[i] != nums[j]) {
                i++;
                nums[i] = nums[j];
                //or nums[++i] = nums[j];
            }
        }
        return i + 1;
    }
}
```



