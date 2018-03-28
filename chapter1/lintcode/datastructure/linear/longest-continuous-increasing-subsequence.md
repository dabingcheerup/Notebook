![](/assets/Screen Shot 2018-03-28 at 2.06.18 PM.png)

#####Idea:
The idea is to use len to record the length of the current continuous increasing subsequence which ends with nums[i], and use max to record the maximum length.

#####Code:


```
public int findLengthOfLCIS(int[] nums) {
        // init max = 1
        int max = 0, len = 0;
        for(int i = 0; i < nums.length; i++) {

            if(i == 0 || nums[i-1] < nums[i]) max = Math.max(max, ++len);
            else len = 1; //重设长度为1，跳出当前循环，i作为开头，继续往下找
        }
        return max;
    }
```



