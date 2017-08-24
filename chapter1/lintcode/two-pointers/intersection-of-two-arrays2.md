![](/assets/Screen Shot 2017-08-23 at 3.17.13 PM.png)
#Analysis
####Idea:
本题的问题与系列中的第一题基本相同，只是需要考虑在intersection中重复的数量。同样利用HashMap记录，不过这次需要记录nums1[]中出现次数，并且在结果的resultMap中记录同时在nums2[]出现的次数。
和Intersection of Two Arrays类似，但是这题要求答案数组中要出现和原数组中相等数量的重复元素（两个数组中重复元素出现次数少的那个）。
第一种方法同样可以利用sort之后再比较，但是这次不用考虑答案数组中是否包含重复元素。
第二种方法可以利用HashMap，将两个数组中元素和重复次数分别存入两个HashMap，然后去两个HashMap中的重复元素和其中重复次数小的作为答案。


```
public class Solution {
    /**
     * @param nums1 an integer array
     * @param nums2 an integer array
     * @return an integer array
     */
    public int[] intersection(int[] nums1, int[] nums2) {
        // Write your code here
        Map<Integer, Integer> map = new HashMap<Integer, Integer>();
        for(int i = 0; i < nums1.length; ++i) {
            if (map.containsKey(nums1[i]))
                map.put(nums1[i], map.get(nums1[i]) + 1); 
            else
                map.put(nums1[i], 1);
        }

        List<Integer> results = new ArrayList<Integer>();

        for (int i = 0; i < nums2.length; ++i)
            if (map.containsKey(nums2[i]) &&
                map.get(nums2[i]) > 0) {
                results.add(nums2[i]);
                map.put(nums2[i], map.get(nums2[i]) - 1); 
            }

        int result[] = new int[results.size()];
        for(int i = 0; i < results.size(); ++i)
            result[i] = results.get(i);

        return result;
    }
}
```

