![](/assets/Screen Shot 2018-01-26 at 11.12.41 AM.png)

#####Idea:
1. 碰到0：max清零，碰到1：max++

```
 public int findMaxConsecutiveOnes(int[] nums) {
        int maxHere = 0, max = 0;
        for (int n : nums)
            max = Math.max(max, maxHere = n == 0 ? 0 : maxHere + 1);
        return max; 
    } 
```