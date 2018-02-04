![](/assets/Screen Shot 2017-08-29 at 8.57.36 PM.png)
#Analysis
####Idea:
Binary search : sorted array, find the first or last position 
#####BS Template
(find + sorted array = binary search)
Template:
    1. initialize: start, end, mid
    2. while(start+1 < end) （最后找到只剩下start和end，然后再和target比较）
        i. mid
        ii.比较mid和target来update start，end（注意：在findFirstPos中，当mid == target，不能直接返回mid的index，因为有可能不是第一个，所以把mid作为end，再往前找）
    3. 结束while后，start和end分别和target比较，哪个和target相同返回哪个。若都不同，返回-1



```
// version 1: with jiuzhang template
class Solution {
    /**
     * @param nums: The integer array.
     * @param target: Target to find.
     * @return: The first position of target. Position starts from 0.
     */
    public int binarySearch(int[] nums, int target) {
        if (nums == null || nums.length == 0) {
            return -1;
        }
        
        int start = 0, end = nums.length - 1;
        while (start + 1 < end) {
            int mid = start + (end - start) / 2;
            if (nums[mid] == target) {
                end = mid;
            } else if (nums[mid] < target) {
                start = mid;
                // or start = mid + 1
            } else {
                end = mid;
                // or end = mid - 1
            }
        }
        
        if (nums[start] == target) {
            return start;
        }
        if (nums[end] == target) {
            return end;
        }
        return -1;
    }
}

```

![](/assets/Screen Shot 2017-08-29 at 9.09.20 PM.png)