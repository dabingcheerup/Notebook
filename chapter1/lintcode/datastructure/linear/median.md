![](/assets/Screen Shot 2017-08-29 at 9.09.31 PM.png)

# Analysis

#### Idea:

Quick sort

这道题可以用快速选择一个类似快速排序的方法。如果数组长度为n,这道题求中位数实际上可以转化为求整个数组当中第\(n+1\)/2大的数，每次选择数组里面最左边的元素然后把数组里面比它大的放在数组它右边，比它小的放在左边，然后知道这个元素是在整个数组当中的第x大.如果x&lt;\(n+1\)/2, 那么可以这个元素右边的数组里面找第\(n+1\)/2大，如果是x&gt;\(n+1\)/2，那么在这个元素左边的数组里面找第\(n+1\)/2大。以此递归的查询。直到x 等于\(n+1\)/2 停止递归。我们采用这种方法的均摊时间复杂度为O\(n\).

```
public class Solution {
    /**
     * @param nums: A list of integers.
     * @return: An integer denotes the middle number of the array.
     */
    public int median(int[] nums) {
        return sub(nums, 0, nums.length - 1, (nums.length + 1)/2);
    }
    private int sub(int[] nums, int start, int end, int size) {
        int mid = (start + end) / 2;
        int pivot = nums[mid];
        int i = start - 1, j = end + 1;
        for (int k = start; k < j; k++) {
            if (nums[k] < pivot) {
                i++;
                int tmp = nums[i];
                nums[i] = nums[k];
                nums[k] = tmp;
            } else if (nums[k] > pivot) {
                j--;
                int tmp = nums[j];
                nums[j] = nums[k];
                nums[k] = tmp;
                k--;
            }
        }
        if (i - start + 1 >= size) {
            return sub(nums, start, i, size);
        } else if (j - start >= size) {
            return nums[j-1];
        } else {
            return sub(nums, j, end, size - (j - start));
        }
    }
}
```

![](/assets/Screen Shot 2017-08-29 at 9.38.26 PM.png)

