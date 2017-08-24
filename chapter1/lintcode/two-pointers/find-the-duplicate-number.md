![](/assets/Screen Shot 2017-08-23 at 3.46.23 PM.png)
#Analysis
####Idea:
我们在区别[1, n]中搜索，首先求出中点mid，然后遍历整个数组，统计所有小于等于mid的数的个数，如果个数大于mid，则说明重复值在[mid+1, n]之间，反之，重复值应在[1, mid-1]之间，然后依次类推，知道搜索完成，此时的low就是我们要求的重复值
二分查找,    1..10,,    小于等于5的一定有5个,如果多于5个,就在lower part, 等于5个就是upper part. 

```
public class Solution {
    /**
     * @param nums an array containing n + 1 integers which is between 1 and n
     * @return the duplicate one
     */
    public int findDuplicate(int[] nums) {
        // Write your code here
        int low = 1, high = nums.length -1;
        while (low <= high) {
            int mid = low + (high - low) /2;
            int count = 0;
            for (int i = 0; i < nums.length; i++) {
                if (nums[i] <= mid) {
                    count++;
                }
            }
            if (count <= mid) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }
        return low;
    }
};
```


