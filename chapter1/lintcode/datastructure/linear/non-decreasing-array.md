##### Idea:

1. cnt 表示改变的次数
2. 当nums[i-1] > nums[i]，根据以下两种情况判断要改的数（画图）

#####Code:


```
public boolean checkPossibility(int[] nums) {
        int cnt = 0;
        for(int i = 1; i < nums.length && cnt <=1; i++) {
            if(nums[i-1] > nums[i]) {
                cnt++;
                //
                if(i < 2 || nums[i-2] <= nums[i]) nums[i-1] = nums[i];  // i < 2
                else {
                    nums[i] = nums[i-1];
                }
            }
        }
        return cnt <= 1;
```



##### Error:

```
for(int i = 1; i < nums.length && cnt <=1; i++) {
            if(nums[i-1] > nums[i]) {
                cnt++;
                //
                if(nums[i-2] <= nums[i]) nums[i-1] = nums[i];  //

java.lang.ArrayIndexOutOfBoundsException: -1
原因：当 i = 1时，i-2不存在。
改：if(i < 2 || nums[i-2] <= nums[i])
```



