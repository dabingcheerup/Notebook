![](/assets/Screen Shot 2017-08-22 at 3.44.32 PM.png)、
#Analysis
####Idea:
1. container的高由短的决定
2. ans记录最大area
3. 左边比右边短 left++ 左边比右边大 right--



```
public class Solution {
    /*
     * @param heights: a vector of integers
     * @return: an integer
     */
    public int maxArea(int[] heights) {
        // write your code here
        if (heights == null || heights.length == 0) {
            return 0;
        }
        int left = 0, ans = 0;
        int right = heights.length - 1;
        while (left <= right) {
            ans = Math.max(ans, (right - left) * Math.min(heights[left], heights[right]));
            if (heights[left] < heights[right]) {
                left++;
            } else {
                right--;
            }
        }
        return ans;
    }
}
```


####难点：
1. 读不懂题【画图】

#### 知识点：
1. coordinate: 坐标 slant: 倾斜++++++++++++